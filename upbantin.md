echo "# auto-upload-bantin" >> README.md
git init
git add upbantin.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/thoitietqtri/auto-upload-bantin.git
git push -u origin main
Hướng dẫn dùng hệ thống up bản tin tự động (04:30 hằng ngày)
Mục tiêu

17:00 hằng ngày: đưa file PDF bản tin (và hồ sơ nếu có) lên GitHub.

04:30 sáng hôm sau: hệ thống tự đăng nhập và up lên website cơ quan.

1) Đăng nhập

Truy cập: https://github.com

Dùng tài khoản bot chung của phòng: (được quản lý bởi trưởng phòng)
→ Nhập mã 2FA từ điện thoại văn phòng (Google/Microsoft Authenticator).

Vào repo: thoitietqtri/auto-upload-bantin

Lưu ý bảo mật: KHÔNG đổi mật khẩu/2FA tài khoản bot. KHÔNG tạo token/ứng dụng lạ.

2) Việc cần làm mỗi ngày lúc 17:00

Trong repo, mở thư mục bantin/
(nếu chưa thấy, chọn Add file → Create new file và gõ bantin/.gitkeep rồi Commit để tạo thư mục).

Bấm Add file → Upload files.

Kéo-thả file PDF bản tin vào khung upload (giữ nguyên tên gốc; KHÔNG đổi tên).

Nếu có hồ sơ kèm theo, kéo thêm file PDF hồ sơ vào cùng thư mục bantin/ (giữ nguyên tên).

Tên hồ sơ thường bắt đầu bằng HS_… hoặc có _HS – cứ để nguyên.

Ở cuối trang:

Commit message: ví dụ Bản tin 2025-08-21 17:00 – (NV: Hạnh)

Chọn Commit directly to the main branch

Commit changes

👉 Là xong phần của bạn. Hệ thống sẽ tự xử lý lúc 04:30.

3) Kiểm tra đã nhận việc chưa (tuỳ chọn)

Mở tab Actions → chọn workflow Auto Upload BanTin.

Nếu muốn chạy thử ngay: bấm Run workflow.

Xem ✔ xanh là OK. Có thể tải Artifacts → upload-proof để xem ảnh chụp màn hình sau khi upload (after_upload.png).

4) Nguyên tắc quan trọng (để không nhầm)

Chỉ thao tác trong thư mục bantin/.
Không xóa/sửa các thư mục khác (.github/, tools/, …).

KHÔNG đổi tên file – để nguyên tên gốc (vd: QTRI_DIEM_20250821_0430.pdf, HS_QTRI_DIEM_20250821_0430.pdf).

Có thể tải nhiều file trong bantin/; hệ thống sẽ tự chọn bản mới nhất theo ngày/giờ trong tên:

Bản tin: file không phải HS.

Hồ sơ: file bắt đầu HS… hoặc có _HS.

Nếu không nhận ra ngày trong tên, hệ thống lấy PDF mới nhất.

Dung lượng web GitHub: mỗi file < 100MB. Nếu lớn hơn, hãy nén/giảm dung lượng trước.

5) Câu hỏi thường gặp & xử lý sự cố

Q1. Không thấy thư mục bantin/?
→ Tạo mới: Add file → Create new file → gõ bantin/.gitkeep → Commit. Rồi vào bantin/ để Upload.

Q2. Lỡ up nhầm vào thư mục gốc?
→ Mở file đó → bấm ✏️ Rename → sửa thành bantin/<tên_cũ>.pdf → Commit (GitHub sẽ tự di chuyển vào thư mục bantin/).

Q3. Actions báo X đỏ / lỗi workflow?

Mở run vừa lỗi → Artifacts → upload-proof → tải after_upload.png & tools/uploader.log.

Báo cho quản trị để xử lý (thường là cần chọn lại dropdown hoặc điều chỉnh website).

Q4. Cần up gấp, không đợi 04:30?
→ Vào Actions → Auto Upload BanTin → Run workflow để chạy ngay.

Q5. Không đăng nhập được tài khoản bot (2FA)?
→ Liên hệ trưởng phòng để lấy mã 2FA từ điện thoại văn phòng hoặc dùng Recovery code (để trong tủ hồ sơ).

6) Tóm tắt 30 giây

Vào repo → bantin/ → Upload files (để nguyên tên gốc).

Ghi commit message + Commit to main.

(Tuỳ chọn) Actions → Run workflow để chạy ngay.

Sáng hôm sau 04:30 hệ thống tự up.

Ghi chú quản trị (chỉ trưởng phòng)

Secrets (user/pass trang web) được lưu ở Settings → Secrets → Actions của repo, không ai nhìn thấy.

Lịch chạy: 30 21 * * * (UTC) ≡ 04:30 ICT.

Script đang tự nhận diện file theo tên ngày; nếu web đổi giao diện cần cập nhật selectors.

Có thể định kỳ dọn bantin/ (giữ 30 ngày gần nhất) cho gọn.
