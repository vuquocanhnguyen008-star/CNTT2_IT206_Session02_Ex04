# Bài 4: Chẩn đoán và "phẫu thuật" prompt sơ sài thành chuẩn CREATE

## Phần 1: Thành phần CREATE bị thiếu

| Bộ phận | Câu lệnh sơ sài | Thiếu | Giải thích ngắn |
|---|---|---|---|
| CSKH | "Viết tin nhắn xin lỗi khách vì hàng giao chậm." | Character, Adjustment, Type | Không có vai trò, không cấm lỗi (đổ lỗi, hứa suông), không nói rõ định dạng |
| Bán hàng | "Tư vấn cho anh khách mua laptop gaming." | Extras, Request chi tiết, Examples | Không có ngân sách, nhu cầu, khuyến mãi, không có mẫu để AI bắt chước |
| Bảo hành | "Báo giá thay màn hình laptop về cho khách." | Character, Type, Adjustment | Không có vai trò kỹ thuật viên, không có bảng giá, không có quy định bảo hành |

## Phần 2: Master Prompt viết lại

### 1. CSKH

```
[C] Bạn là chuyên viên Chăm sóc khách hàng của TechShop, giọng văn lịch sự, đồng cảm.
[R] Viết tin nhắn xin lỗi khách có đơn hàng giao chậm, thông báo ngày giao dự kiến mới và cách bù đắp.
[E] Ví dụ giọng văn: "TechShop thành thật xin lỗi anh/chị vì sự bất tiện này. Chúng tôi hiểu việc chờ đợi rất khó chịu."
[A] Không đổ lỗi cho đơn vị vận chuyển, không hứa suông, không dùng từ quá máy móc.
[T] Tin nhắn dưới 120 từ gồm: lời xin lỗi, nguyên nhân ngắn gọn, ngày giao mới, phương án bù đắp.
[E] Thông tin: mã đơn [..], ngày giao mới [..], voucher [..], hotline [..].
```

### 2. Bán hàng

```
[C] Bạn là nhân viên tư vấn bán laptop gaming của TechShop, am hiểu phần cứng.
[R] Tư vấn cho khách có ngân sách [..] triệu, chơi game [..], cần máy gọn nhẹ/hiệu năng cao.
[E] Ví dụ: "Với 25 triệu, anh nên chọn máy A vì card RTX 4050 chạy mượt game X ở mức High."
[A] Chỉ gợi ý 3 máy trong tầm giá, không liệt kê dài, không nói quá về sản phẩm.
[T] Bảng gồm: tên máy, cấu hình chính, giá, điểm mạnh, điểm yếu, kèm 1 câu khuyến nghị.
[E] Khuyến mãi đang có: [..], chính sách bảo hành, trả góp.
```

### 3. Bảo hành

```
[C] Bạn là kỹ thuật viên bảo hành của TechShop.
[R] Báo giá thay màn hình laptop cho khách theo đúng model máy.
[E] Ví dụ: "Dell Inspiron 15 3520, màn FHD: 1.800.000đ, thời gian 2 ngày."
[A] Không trả lời chung chung "tùy model", nếu thiếu model thì hỏi lại khách.
[T] Bảng báo giá: model, loại màn hình, giá linh kiện, công thay, thời gian, bảo hành.
[E] Bảng giá tham chiếu và quy định bảo hành của TechShop [dán vào đây].
```
