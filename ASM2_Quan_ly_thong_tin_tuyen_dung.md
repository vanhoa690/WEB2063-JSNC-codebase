# BÀI KIỂM TRA ASM 2 – QUẢN LÝ THÔNG TIN TUYỂN DỤNG

## JavaScript nâng cao + HTML/CSS + Axios + JSON Server

**Thời gian:** 60 phút  
**Tổng điểm:** 10 điểm  
**Hình thức:** Thực hành cá nhân

---

# I. ĐỀ BÀI

Xây dựng ứng dụng **Job Management – Quản lý thông tin tuyển dụng** bằng JavaScript thuần, HTML/CSS, Axios và JSON Server.

**Không sử dụng React, TypeScript hoặc thư viện giao diện.**

Ứng dụng cần có các chức năng:

- Hiển thị danh sách tin tuyển dụng.
- Thêm, sửa và xóa tin tuyển dụng.
- Đăng ký tài khoản.
- Đăng nhập và đăng xuất.
- Lưu trạng thái đăng nhập bằng `localStorage`.
- Bảo vệ các trang quản lý, chỉ cho phép người dùng đã đăng nhập truy cập.

## 1. Công nghệ và kiến thức sử dụng

- HTML/CSS để xây dựng giao diện.
- JavaScript thao tác DOM: `querySelector`, `addEventListener`, `innerHTML`.
- Axios với các request `GET`, `POST`, `PUT`, `DELETE`.
- Bất đồng bộ với `async/await`.
- Xử lý lỗi với `try/catch/finally`.
- Kiểm tra dữ liệu form.
- Sử dụng `localStorage` để lưu trạng thái đăng nhập.
- Sử dụng `session` hoặc trạng thái đăng nhập phía trình duyệt để kiểm soát quyền truy cập trang.
- Điều hướng giữa các trang bằng liên kết hoặc JavaScript.

## 2. API sử dụng

- Danh sách tin tuyển dụng: `http://localhost:3000/vacancies`
- Danh sách tài khoản: `http://localhost:3000/users`

Khởi chạy JSON Server bằng lệnh phù hợp với phiên bản đã học, ví dụ:

```bash
npm run db
```

## 3. Dữ liệu mẫu

Tạo file `db.json` với nội dung:

```json
{
  "users": [],
  "vacancies": [
    {
      "id": "1",
      "positionName": "Frontend Developer",
      "employer": "FPT Software",
      "workplace": "Hà Nội",
      "monthlyIncome": 15000000,
      "workType": "Full-time",
      "jobDetails": "Phát triển giao diện web."
    },
    {
      "id": "2",
      "positionName": "Backend Developer",
      "employer": "CMC Global",
      "workplace": "Hà Nội",
      "monthlyIncome": 18000000,
      "workType": "Full-time",
      "jobDetails": "Phát triển API bằng Node.js."
    },
    {
      "id": "3",
      "positionName": "UI/UX Designer",
      "employer": "VNG Corporation",
      "workplace": "TP. Hồ Chí Minh",
      "monthlyIncome": 12000000,
      "workType": "Part-time",
      "jobDetails": "Thiết kế giao diện người dùng."
    },
    {
      "id": "4",
      "positionName": "Intern React Developer",
      "employer": "Tech Company",
      "workplace": "Đà Nẵng",
      "monthlyIncome": 5000000,
      "workType": "Internship",
      "jobDetails": "Hỗ trợ phát triển ứng dụng."
    },
    {
      "id": "5",
      "positionName": "Tester",
      "employer": "ABC Technology",
      "workplace": "Hà Nội",
      "monthlyIncome": 10000000,
      "workType": "Full-time",
      "jobDetails": "Kiểm thử chức năng ứng dụng."
    }
  ]
}
```

---

# II. NỘI DUNG KIỂM TRA

## Câu 1 – Hiển thị danh sách tin tuyển dụng (2,0 điểm)

Sử dụng Axios để lấy danh sách tin tuyển dụng từ API:

```http
GET /vacancies
```

Hiển thị danh sách dưới dạng bảng với các cột:

- STT.
- Tên công việc.
- Công ty tuyển dụng.
- Địa điểm.
- Mức lương.
- Hình thức làm việc.
- Chức năng.

## Câu 2 – Thêm tin tuyển dụng mới (2,0 điểm)

Tạo form thêm tin tuyển dụng với các trường:

- Tên công việc.
- Tên công ty.
- Địa điểm.
- Mức lương.
- Hình thức làm việc.
- Mô tả công việc.

Hình thức làm việc được chọn từ danh sách:

- Full-time.
- Part-time.
- Internship.

Khi nhấn nút **Thêm tin tuyển dụng**, gửi request:

```http
POST /vacancies
```

### Yêu cầu

3. Các trường bắt buộc không được để trống.
4. Mức lương phải là số hợp lệ lớn hơn 0.
5. Hình thức làm việc phải thuộc danh sách cho phép.
6. Thêm thành công thì thông báo
7. Hiển thị thông báo lỗi nếu không thêm được tin tuyển dụng.

## Câu 3 – Sửa và xóa tin tuyển dụng (2,0 điểm)

### a. Sửa tin tuyển dụng (1,0 điểm)

Mỗi dòng tin tuyển dụng có nút **Sửa**.

Khi nhấn nút Sửa, đưa thông tin hiện tại của tin tuyển dụng lên form.

Khi nhấn nút **Cập nhật**, gửi request:

```http
PUT /vacancies/:id
```

**Yêu cầu:**

1. Hiển thị đúng thông tin của tin tuyển dụng được chọn.
2. Lưu lại `id` của tin tuyển dụng đang sửa để phân biệt thao tác thêm mới và cập nhật.
3. Kiểm tra dữ liệu trước khi cập nhật.
4. Cập nhật thành công thì hiển thị dữ liệu mới trên bảng.
5. Không tạo thêm bản ghi mới khi cập nhật.
6. Xử lý lỗi khi API cập nhật thất bại.

### b. Xóa tin tuyển dụng (1,0 điểm)

Mỗi dòng tin tuyển dụng có nút **Xóa**.

Khi nhấn nút Xóa, gửi request:

```http
DELETE /vacancies/:id
```

**Yêu cầu:**

1. Sử dụng `confirm()` để xác nhận trước khi xóa.
2. Chỉ gửi request khi người dùng xác nhận.
3. Sau khi xóa thành công, cập nhật danh sách trên giao diện mà không tải lại trang.
4. Hiển thị thông báo khi xóa thành công hoặc thất bại.

## Câu 4 – Đăng ký và đăng nhập tài khoản (2,0 điểm)

Xây dựng giao diện đăng ký và đăng nhập bằng HTML/CSS và JavaScript.

### a. Đăng ký tài khoản (1,0 điểm)

Form đăng ký gồm các trường:

- Username.
- Email.
- Password.
- Confirm Password.

Khi nhấn nút **Đăng ký**, thực hiện kiểm tra dữ liệu và gửi request:

```http
POST /users
```

Dữ liệu tài khoản lưu theo cấu trúc:

```json
{
  "username": "student01",
  "email": "student01@example.com",
  "password": "123456"
}
```

**Yêu cầu:**

1. Username không được để trống.
2. Email phải đúng định dạng cơ bản.
3. Password tối thiểu 6 ký tự.
4. Confirm Password phải trùng với Password.
5. Không cho phép đăng ký username đã tồn tại.
6. Sử dụng Axios để lưu tài khoản vào JSON Server.
7. Đăng ký thành công thì thông báo và điều hướng đến trang Login.
8. Xử lý lỗi khi đăng ký thất bại.
9. emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

### b. Đăng nhập và đăng xuất (1,0 điểm)

Form đăng nhập gồm:

- Email.
- Password.

Sử dụng Axios để lấy danh sách tài khoản:

```http
GET /users
```

Kiểm tra email và password người dùng nhập với dữ liệu tài khoản.

**Yêu cầu:**

1. Username và Password không được để trống.
2. Đăng nhập đúng thì lưu thông tin phiên đăng nhập vào `localStorage`.
3. Đăng nhập thành công thì điều hướng đến trang `/` hoặc trang danh sách tuyển dụng tương ứng trong ứng dụng.
4. Đăng nhập sai thì hiển thị thông báo lỗi.
5. Khi đã đăng nhập, hiển thị thông tin người dùng và nút Logout.
6. Khi nhấn Logout, xóa thông tin phiên đăng nhập khỏi `localStorage` và điều hướng về trang Login.

## Câu 5 – Bảo vệ trang quản lý tuyển dụng (2,0 điểm)

Sử dụng JavaScript để kiểm tra trạng thái đăng nhập trước khi cho phép người dùng truy cập các trang quản lý.

### Các trang yêu cầu

| Trang            | Chức năng            | Quyền truy cập |
| ---------------- | -------------------- | -------------- |
| `login.html`     | Đăng nhập            | Công khai      |
| `register.html`  | Đăng ký              | Công khai      |
| `index.html`     | Danh sách tuyển dụng | Phải đăng nhập |
| `add.html`       | Thêm tin tuyển dụng  | Phải đăng nhập |
| `edit.html?id=1` | Sửa tin tuyển dụng   | Phải đăng nhập |

### Yêu cầu

1. Xây dựng hàm kiểm tra trạng thái đăng nhập, ví dụ `checkAuth()`.
2. Sử dụng `localStorage` để xác định người dùng đã đăng nhập hay chưa.
3. Nếu chưa đăng nhập mà truy cập trang danh sách, thêm hoặc sửa tin tuyển dụng, điều hướng về trang Login.
4. Nếu đã đăng nhập, cho phép truy cập các trang quản lý.
5. Khi tải lại trang, khôi phục trạng thái đăng nhập từ `localStorage`.
6. Khi đăng xuất, người dùng phải đăng nhập lại mới được truy cập các trang được bảo vệ.
7. Chỉ hiển thị chức năng thêm, sửa, xóa khi người dùng đã đăng nhập.

---

# IV. TỔNG KẾT THANG ĐIỂM

| Nội dung                                        |     Điểm |
| ----------------------------------------------- | -------: |
| Câu 1 – Hiển thị danh sách, Loading và Error    |      2,0 |
| Câu 2 – Thêm tin tuyển dụng và kiểm tra dữ liệu |      2,0 |
| Câu 3 – Sửa và xóa tin tuyển dụng               |      2,0 |
| Câu 4 – Đăng ký, đăng nhập và đăng xuất         |      2,0 |
| Câu 5 – Bảo vệ trang quản lý                    |      2,0 |
| **Tổng cộng**                                   | **10,0** |

---

## Câu 6 -- Tìm kiếm bằng JSON Server

Tạo ô nhập tìm kiếm theo tên.

Ví dụ request:

```http
GET /vacancies?title_like=Frontend
```

## Câu 7 -- Nâng cao: Sắp xếp dữ liệu từ API

Bổ sung hai danh sách lựa chọn:

```text
Sắp xếp theo: [Lương ▼]
Thứ tự:       [Giảm dần ▼]
```

**Sắp xếp theo:**

- Lương (`monthlyIncome`)
- Id (`id`)

**Thứ tự:**

- Tăng dần (`asc`)
- Giảm dần (`desc`)

### Ví dụ request

Sắp xếp theo năm phát hành giảm dần:

```http
GET /vacancies?_sort=monthlyIncome&_order=desc
```

Tìm tin có tên chứa `Frontend`, sau đó sắp xếp theo lương tăng dần:

```http
GET /vacancies?title_like=Frontend&_sort=monthlyIncome&_order=asc
```
