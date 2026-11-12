# Báo cáo thực hành Day 3

- **Mã học viên theo lớp:** 2A202603272
- **Ngày / CVAT local:** 11/11/2026
- **Công cụ đã dùng:** CVAT, Segment Anything 3

## 1. Bài đã nộp

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
|---|---|---:|---:|
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | `cp1_holes.zip` | 1 / 1 | 3 |
| cp2_slice | `cp2_slice.zip` | 1 / 1 | 3 |
| cp5_occlusion | `cp5_occlusion.zip` | 1 / 1 | 3 |
| cp3_thin | `cp3_thin.zip` | 1 / 1 | 3 |
| cp4_curb | `cp4_curb.zip` | 1 / 1 | 3 |
| cp6_coverage | `cp6_coverage.zip` | 1 / 1 | 3 |
| **Tổng tối đa** | | **14 / 14** | **100** |

Các task chính Easy, Medium và Hard đã hoàn thành. Các checkpoint cũng đã được hoàn thiện, sử dụng tên ZIP tương ứng với yêu cầu của từng task.

## 2. Một quyết định trước khi dùng gợi ý

- **Ảnh, vị trí và object Medium đầu tiên tự vẽ:** Ảnh giao thông đường phố, object car ở khu vực lòng đường.
- **Class và quy tắc tôi dùng để chọn biên:** Chọn class car. Tôi xác định đường biên dựa trên hình dáng thực tế của xe, chỉ lấy phần thuộc về xe và không bao gồm mặt đường hoặc phương tiện bên cạnh.
- **Nếu dùng gợi ý sau đó:** Tôi sử dụng Segment Anything 3 để hỗ trợ tạo mask. Sau khi có gợi ý, tôi kiểm tra lại đường biên, đặc biệt tại những vị trí xe nằm gần nhau hoặc bị che khuất.
- **Quyết định:** Ưu tiên mask riêng cho từng object, không gộp các phương tiện khác nhau thành một mask.

## 3. Một lỗi tôi tìm thấy và sửa

- **Task/ảnh/vùng:** Các task checkpoint, đặc biệt là CP1, CP2, CP3, CP4 và CP6.
- **Lỗi thuộc loại:** Khác – định dạng export và tên file chưa đúng yêu cầu.
- **Bằng chứng tôi nhìn thấy:** Một số file ZIP ban đầu có tên chưa đúng quy định hoặc chứa `annotations.xml` thay vì định dạng dataset được yêu cầu.
- **Quy tắc và hành động sửa:** Kiểm tra lại định dạng export của từng task, xuất đúng định dạng và đặt tên ZIP theo tên task tương ứng. Đồng thời kiểm tra lại annotation trước khi hoàn tất.
- **Sau sửa đã Save và export lại chưa?:** Đã Save và hoàn thiện các file ZIP theo tên yêu cầu.
- **Kết quả Summary:** Easy đạt 20/20, Medium đạt 20.1/32, Hard đạt 19.2/30. Tổng điểm ba tier là **59.3/82**. Chưa có metric trước và sau sửa cho lỗi cụ thể.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
|---|---|---|---|
| [Ảnh 1 – 000000350023.jpg](../../data/tiers/hard_panoptic/images/000000350023.jpg), các ô tô nhỏ ở xa trên đường | Gộp các xe gần nhau thành một vùng hoặc tách từng xe riêng biệt | Các xe có kích thước nhỏ nhưng vẫn có thể nhận diện đường viền riêng | Ưu tiên tách từng xe thành instance riêng nếu có thể xác định được từng object. |
| [Ảnh 2 – 000000460147.jpg](../../data/tiers/hard_panoptic/images/000000460147.jpg), xe chở ô tô ở giữa ảnh | Gán một mask cho xe vận chuyển hoặc tạo mask riêng cho từng ô tô trên xe | Nhiều ô tô nằm sát nhau và một phần bị che khuất | Cần xác nhận các ô tô đang được vận chuyển có cần được gán instance riêng không. |
| [Ảnh 3 – 000000373353.jpg](../../data/tiers/medium_instance/images/000000373353.jpg), người đi bộ trước taxi và xe buýt | Gán mask riêng cho người đi bộ hoặc lấy cả phần bị che khuất phía sau | Người đi bộ đứng trước taxi và xe buýt, có sự chồng lấp giữa các object | Chỉ gán phần nhìn thấy của người đi bộ, không lấy phần thuộc về phương tiện phía sau. |

## Kết luận

Qua Day 3, tôi đã thực hành semantic segmentation, instance segmentation và panoptic segmentation trên các ảnh giao thông đường phố.

Tôi chú ý hơn đến việc xác định class, phân biệt từng object, lựa chọn đường biên và xử lý các vùng bị che khuất. Ngoài ra, tôi đã sử dụng Segment Anything 3 để hỗ trợ quá trình tạo mask và kiểm tra lại kết quả trước khi lưu.

Tôi đã hoàn thành các task chính và checkpoint, đồng thời kiểm tra lại tên file và định dạng export để chuẩn bị nộp bài.