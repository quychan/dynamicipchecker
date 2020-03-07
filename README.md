# Dynamic IP Checker

## GIẢI QUYẾT VẤN ĐỀ GÌ?

1. Ở nhà không có IP tĩnh, IP bị thay đỗi liên tục (do reset router hoặc lâu lâu nhà mạng đỗi hoặc cúp điện v.v... )

2. Bạn không muốn dùng một phần mềm mà bạn không biết rõ nó là gì (ví dụ như NoIP).

Nếu bạn gặp phải những vấn đề sau thì sử dụng Project phía dưới là hợp lý rồi

## NGUYÊN LÝ HOẠT ĐỘNG

Mục tiêu cuối cùng là kiểm tra IP máy hiện tại của bạn đang là bao nhiêu và sau đó so sánh với IP của tên miền đang được trỏ tới có trùng hay không.

1. Nếu trùng sẽ tiếp tục kiểm tra sau N giây (N là thời gian bạn cấu hình trong tệp tin) (1)

2. Nếu KHÔNG trùng, sẽ gửi một request lên CloudFlare để yêu cầu CloudFlare trỏ tên miền con (support only subdomain for now) đó về IP hiện tại và sau đó trở về (1).

## CÀI ĐẶT

Bạn cần phải cài đặt bằng tay các bước hướng dẫn sau:

## Những thứ cần chuẩn bị cho tên miền

1. Một tên miền đã trỏ tới CloudFlare

2. Đăng ký một tài khoản CloudFlare

3. Tạo một subdomain (A record) và trỏ subdomain đó về một IP bất kỳ

## Những thứ cần chuẩn bị cho máy chủ (Hướng dẫn này chỉ áp dụng cho Linux)

1. Tự động chạy nếu vô tình bị Reset hoặc Reboot

Tạo file /etc/systemd/systemd/dynamicipchecker.service với nội dung như sau:

updating...

2. Bộ source được cài đặt ở folder bất kỳ

Mình khuyến khích các bạn cài đặt vào folder /opt/dynamicipchecker/

## Cấu Hình Mã Nguồn

Vào file /opt/dynamicipchecker/config.php để chỉnh sửa các file sau:

1. $domain = 'example.com';

2. $subdomain = 'homeip';

3. $sleepTime = 600; # Thời gian ngủ

4. $cloudFlareToken = '';