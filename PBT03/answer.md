PHẦN A - KIỂM TRA ĐỌC HIỂU
Câu A1:
---Inline---: 
<h2 style="color: blue; font-size: 24px;">Đây là tiêu đề màu xanh</h2>

Ưu điểm: Áp dụng nhanh chóng cho một phần tử duy nhất, không cần tạo file hoặc viết vùng chọn (selector) phức tạp. Có độ ưu tiên rất cao.

Nhược điểm: Làm code HTML trở nên rối rắm, khó đọc. Khó bảo trì vì nếu muốn sửa giao diện của nhiều thẻ giống nhau, bạn phải sửa từng thẻ một. Không tái sử dụng được code.

Khi nào nên dùng:
-Khi cần test nhanh một thuộc tính CSS.

-Khi muốn áp dụng một style đặc biệt, duy nhất cho một phần tử mà không muốn viết thêm vào file CSS chung.

---Internal---
<head>
    <style>
        p {
            color: green;
            line-height: 1.6;
        }
    </style>
</head>
<body>
    <p>Đoạn văn này sẽ có chữ màu xanh lá cây.</p>
</body>

Ưu điểm: Quản lý style của toàn bộ một trang web tại một nơi duy nhất. Có thể sử dụng các vùng chọn (class, id, tag) để áp dụng cho nhiều phần tử cùng lúc trong trang đó.

Nhược điểm: Chỉ có tác dụng trong phạm vi trang hiện tại, không thể tái sử dụng cho các trang khác trong cùng một website. Nếu viết quá nhiều CSS, file HTML sẽ rất dài.

Khi nào nên dùng
-Khi bạn đang viết một website đơn trang hoặc một trang đích độc lập.

-Khi trang đó có phong cách thiết kế hoàn toàn khác biệt với phần còn lại của website.

---External---

.btn-submit {
    background-color: red;
    color: white;
    padding: 10px 20px;
}
Ưu điểm: Tách biệt hoàn toàn giữa nội dung (HTML) và giao diện (CSS). Có thể dùng chung một file CSS cho hàng trăm trang web khác nhau, giúp website đồng bộ và cực kỳ dễ bảo trì. Trình duyệt có thể lưu bộ nhớ đệm (cache) file CSS giúp trang tải nhanh hơn ở các lần sau.

Nhược điểm: Tạo thêm một yêu cầu tải file (HTTP Request) từ server, nếu file CSS chưa tải xong thì trang web có thể bị lỗi hiển thị trong tích tắc.

Khi nào nên dùng
-Luôn luôn là lựa chọn ưu tiên hàng đầu khi xây dựng một trang web thực tế, đặc biệt là các website có từ 2 trang trở lên.

Câu A2
1. h1                           → Chọn: ShopTLU
2. .price                       → Chọn: 25.990.000đ / 45.990.000đ
3. #app header                  → Chọn: ShopTLU/Home/Products/About
4. nav a:first-child             → Chọn: Home
5. .product.featured h2         → Chọn: Macbook Pro
6. article > p                  → Chọn: 25.990.000đ/ Mô tả sản phẩm/45.990.000đ/Mô tả sản phẩm
7. a[href="/"]                  → Chọn: Home
8. .top-bar.dark h1              → Chọn: ShopTLU

Câu A3:
/* Trường hợp 1: content-box (mặc định) */
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = 450px
→ Không gian chiếm trên trang = 470px

/* Trường hợp 2: border-box */
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = 400px
→ Kích thước content thực tế = 350px
→ Không gian chiếm trên trang = 420px

/* Trường hợp 3: Margin collapse */
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
→ Khoảng cách giữa box-a và box-b = 40px
→ Giải thích tại sao KHÔNG PHẢI 65px
Trong CSS, khi hai khối nằm dọc chồng lên nhau, các lề dọc (margin-top và margin-bottom) của chúng sẽ xảy ra hiện tượng Margin Collapse (Sụp đổ lề). Thay vì cộng dồn vào nhau (25px + 40px = 65px), trình duyệt sẽ so sánh và chỉ lấy giá trị lớn nhất làm khoảng cách giữa hai khối. Vì 40px > 25px nên khoảng cách thực tế là 40px

Nếu .box-a có margin-bottom: -10px và .box-b có margin-top: 40px, khoảng cách = bao nhiêu?
Khoảng cách thực tế: 30px
Quy tắc tính Margin Collapse khi có số âm:Nếu có sự kết hợp giữa lề dương và lề âm, trình duyệt sẽ lấy lề dương lớn nhất cộng với lề âm nhỏ nhất (âm nhất).Ở đây ta có:Lề dương lớn nhất = 40px, Lề âm nhỏ nhất = -10px 
Kết quả: 40px - 10px = 30px (Hai khối này sẽ bị hút lại gần nhau hơn, đè lên nhau một chút).

Câu A4:
1. Tính specificity score (a, b, c) cho mỗi rule
Dựa vào quy tắc trên, ta tính được điểm số của từng dòng như sau:
    Rule A (p): Chỉ có 1 thẻ HTML
        -> Score: (0,0,1)
    Rule B (.price): Chỉ có 1 Class
        -> Score: (0,1,0)
    Rule C (#main-price): Chỉ có 1 ID
        -> Score: (1,0,0)
    Rule D (p.price): Gồm 1 thẻ HTML (p) và 1 Class 
        -> Score: (0,1,1)
2. Element sẽ có màu gì?
 Kết quả: Element sẽ có màu đỏ.
 Trình duyệt sẽ so sánh điểm số từ trái qua phải (so sánh a trước, nếu a bằng nhau mới so sánh đến b, rồi đến c).
 Rule C có điểm a = 1 (do dùng ID selector #main-price), trong khi tất cả các Rule khác đều có a = 0. Vì (1, 0, 0) > (0, 1, 1) > (0, 1, 0) > (0, 0, 1), nên Rule C có độ ưu tiên cao nhất tuyệt đối trong 4 rules này.
3. Nếu thêm style nội dòng, element có màu gì?
Đoạn code: <p class="price" id="main-price" style="color: orange;">
Kết quả: Element đổi sang màu cam.
Kỹ thuật nhúng CSS trực tiếp vào thẻ HTML thông qua thuộc tính style (Inline CSS) có cấp độ ưu tiên vượt lên trên tất cả các bộ chọn ID, Class hay Element viết trong file CSS bên ngoài. Nó tương đương với một mức điểm nằm ở hàng cao hơn cả a (thường được ví là cột thứ 4: (1, 0, 0, 0)).
4. Nếu Rule A thêm !important, element có màu gì? Tại sao?Đoạn code khi sửa: p { color: black !important; }
Kết quả: Element sẽ có màu đen.
Từ khóa !important trong CSS không tham gia vào thang điểm số (a, b, c) thông thường mà nó là một "lệnh phá vỡ quy tắc". Khi bạn gắn !important vào sau một thuộc tính, bạn đang ra lệnh cho trình duyệt: "Bất kể các vùng chọn khác có điểm cao thế nào, hay thậm chí có dùng Inline CSS đi nữa, hãy bỏ qua hết và bắt buộc phải dùng giá trị này". Do đó, Rule A vốn có điểm thấp nhất lại quay xe thắng cuộc hoàn toàn.

Câu B2
Hộp 1 (content-box): chiều rộng thực tế = 350px px (đo từ DevTools)
Hộp 2 (border-box): chiều rộng thực tế = 300px (đo từ DevTools)
Giải thích sự khác biệt:
Với content-box, giá trị width: 300px chỉ áp dụng cho phần nội dung bên trong. Khi thêm padding và border, kích thước thực tế của hộp sẽ tăng lên.
Cụ thể: 300px + 40px padding + 10px border = 350px. Vì vậy hộp hiển thị lớn hơn kích thước đã khai báo.

Với border-box, giá trị width: 300px là kích thước tổng của cả hộp, đã bao gồm content, padding và border. Trình duyệt sẽ tự động giảm phần content để tổng chiều rộng vẫn giữ nguyên 300px.
