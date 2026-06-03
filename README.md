# Báo cáo thực hành kiểm thử hiệu năng với JMeter

## 1. Giới thiệu

Apache JMeter là một công cụ mã nguồn mở dùng để kiểm thử hiệu năng, kiểm thử tải và đo thời gian phản hồi của hệ thống. Trong bài thực hành này, em sử dụng JMeter để tạo các request kiểm thử đơn giản, chạy test và quan sát kết quả thông qua Aggregate Report.

## 2. Mục tiêu bài thực hành

- Tìm hiểu công cụ Apache JMeter.
- Biết cách tạo Test Plan trong JMeter.
- Biết cách tạo Thread Group và HTTP Request.
- Biết cách chạy kiểm thử hiệu năng.
- Biết cách đọc các thông số như Average, Min, Max, Throughput và Error %.
- Đưa sản phẩm lên GitHub để nộp bài.

## 3. Công cụ sử dụng

- Apache JMeter 5.6.3
- Java JDK
- GitHub
- Trình duyệt web
- Hệ điều hành Windows

## 4. Các bước thực hiện

### Bước 1: Cài đặt JMeter

Em tải Apache JMeter, giải nén và chạy file `jmeter.bat` trong thư mục `bin`.

Sau khi chạy thành công, giao diện Apache JMeter được mở ra.

### Bước 2: Tạo Test Plan

Trong JMeter, em tạo một Test Plan mới, sau đó thêm Thread Group để mô phỏng người dùng gửi request đến hệ thống.

Cấu hình Thread Group:

- Number of Threads: 1
- Ramp-up Period: 1
- Loop Count: 1

### Bước 3: Tạo HTTP Request

Trong Thread Group, em thêm hai HTTP Request.

#### Request 1: google speed test

- Protocol: https
- Server Name: www.google.com
- Path: /search
- Parameter:
  - Name: q
  - Value: speed test

#### Request 2: calculator

- Protocol: https
- Server Name: www.google.com
- Path: /search
- Parameter:
  - Name: q
  - Value: calculator

### Bước 4: Thêm Listener

Em thêm Listener `Aggregate Report` để xem kết quả kiểm thử.

Aggregate Report giúp quan sát các thông số như:

- Samples
- Average
- Median
- Min
- Maximum
- Error %
- Throughput

## 5. Kết quả kiểm thử

Sau khi chạy test, em thu được kết quả trong Aggregate Report.

| Tên test | Samples | Average | Error % |
|---|---:|---:|---:|
| google speed test | 1 | 0 ms | 100.00% |
| calculator | 1 | 1948 ms | 100.00% |
| TOTAL | 2 | 974 ms | 100.00% |

## 6. Nhận xét kết quả

Chỉ số Average thể hiện thời gian phản hồi trung bình của request. Trong bài thực hành này, request `calculator` có thời gian phản hồi trung bình là 1948 ms.

Tuy nhiên, kết quả kiểm thử có Error % là 100.00%, điều này cho thấy các request chưa chạy thành công hoàn toàn. Nguyên nhân có thể do cấu hình request chưa đúng, Google chặn request tự động, hoặc server trả về phản hồi không như mong đợi.

Vì vậy, khi kiểm thử hiệu năng thực tế, cần kiểm tra thêm bằng View Results Tree để xem chi tiết lỗi và điều chỉnh lại cấu hình request.

## 7. Ý nghĩa các thông số trong JMeter

### Average

Average là thời gian phản hồi trung bình của các request. Chỉ số này càng thấp thì hệ thống phản hồi càng nhanh.

### Min

Min là thời gian phản hồi nhỏ nhất trong quá trình kiểm thử.

### Maximum

Maximum là thời gian phản hồi lớn nhất trong quá trình kiểm thử.

### Throughput

Throughput cho biết số lượng request được xử lý trong một đơn vị thời gian.

### Error %

Error % cho biết tỷ lệ request bị lỗi. Nếu Error % cao, cần kiểm tra lại cấu hình request hoặc trạng thái server.

## 8. Kết luận

Qua bài thực hành này, em đã biết cách sử dụng Apache JMeter để tạo Test Plan, thêm Thread Group, tạo HTTP Request và xem kết quả kiểm thử bằng Aggregate Report.

JMeter là công cụ hữu ích trong kiểm thử hiệu năng phần mềm, giúp đánh giá thời gian phản hồi, khả năng xử lý request và phát hiện các vấn đề liên quan đến hiệu năng của hệ thống.
