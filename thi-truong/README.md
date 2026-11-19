# Market Pulse (/thi-truong/)

Trang chu kỳ vĩ mô và khung phân bổ dòng tiền. Cập nhật thủ công, KHÔNG dùng bot hay GitHub Actions commit tự động.

## Cách cập nhật
1. Chạy skill `dt-13-chu-ky-vi-mo` (plugin phong-dau-tu) để có số liệu mới.
2. Sửa `thi-truong/data.json` theo cấu trúc dưới, commit vào `main`. Cloudflare Pages tự deploy.
3. `index.html` tự đọc `data.json` khi tải trang; phần HTML tĩnh trong `index.html` chỉ là bản dự phòng. Muốn bản dự phòng khớp số mới thì chạy lại `build.py` (trong phiên Claude) rồi commit `index.html`.

## Cấu trúc data.json
- `updated`: YYYY-MM-DD
- `note`: một câu miễn trừ
- `cycle[]`: `id`, `name`, `phase` (Phục hồi | Mở rộng | Đỉnh | Suy thoái | Đáy), `tilt`, `axes.growth|inflation|policy` = `{dir: up|flat|down, evidence}`, `sectors`, `counter` (mặt trái), `trigger` (khi nào đổi pha)
- `allocation.classes[6]`, `allocation.profiles[]` = `{name, neutral[6], current[6]}` (mỗi mảng tổng 100), `allocation.reasons[]`, `allocation.rules`
- `sources[]` = `{label, url}` (chỉ https)

Mọi chuỗi được hiển thị bằng textContent, không chèn HTML.
