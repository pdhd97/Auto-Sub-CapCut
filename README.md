# Auto Sub CapCut

Tool tự động làm phụ đề và lồng tiếng Việt cho video. Mở video, bấm **✦ Xử lý video**: tool nghe lời nói, dịch sang tiếng Việt, đọc thành giọng Việt khớp thời gian, che phụ đề gốc, rồi xuất ra video MP4 hoặc dự án CapCut để chỉnh tiếp.

**Tải về:** vào [Releases](https://github.com/pdhd97/Auto-Sub-CapCut/releases/latest), tải `Auto-Sub-Capcut-Setup-<phiên bản>.exe` rồi chạy. Bộ cài đã có sẵn mọi thứ cần dùng (FFmpeg, Python, nhận dạng giọng nói, giọng đọc VieNeu, công cụ dò chữ), không phải cài thêm gì. Để dịch, bạn cần một API key Gemini; trong tool có video hướng dẫn lấy key. Các bản sau tool tự cập nhật.

## Giao diện tool

![Giao diện Auto Sub CapCut](docs/giao-dien-tool.webp)

- **Cột trái: cài đặt**
  - **Nhận dạng giọng nói:** ngôn ngữ nguồn (để Tự động là tool tự nhận ra), cách nhận dạng (CapCut nhanh nhất, CapCut + Gemini chính xác hơn, Whisper). Có thể nhập file SRT/VTT có sẵn.
  - **Dịch thuật:** ngôn ngữ đích, phong cách dịch (tự nhiên, kể chuyện, cổ trang, kiếm hiệp, kinh dị, anime…), ô lưu ý cho AI (tên nhân vật, cách xưng hô). Chọn hiển thị bản dịch sát nghĩa hoặc bản đã rút gọn cho khớp giọng đọc.
  - **Thuyết minh:** chế độ tốc độ đọc (tự động 1.0–1.3x), giọng đọc, âm lượng, che phụ đề gốc, kiểu chữ phụ đề.
- **Giữa: xem trước.** Video phát cùng giọng lồng tiếng và phụ đề tiếng Việt, đúng như khi xuất.
  - Bên dưới là **timeline** gồm phụ đề gốc, phụ đề dịch và voice.
  - Dòng trạng thái cho biết đã khớp bao nhiêu câu, bao nhiêu câu phải giãn thời gian, bao nhiêu đoạn video được làm chậm để giọng đọc vừa.
- **Cột phải: danh sách phụ đề.** Mỗi câu có:
  - nhân vật và giọng đọc riêng (tool tự nhận ra nhân vật và gán giọng nam/nữ);
  - phụ đề gốc, bản dịch sát nghĩa và "phụ đề khớp" (bản rút gọn được đọc);
  - độ dài giọng đọc, tốc độ;
  - nút nghe thử và tạo lại voice.

  Sửa chữ ở đây rồi bấm Voice là có giọng mới.
- **Góc dưới phải: ✦ Xử lý video.** Một nút chạy hết các bước: nhận dạng → dịch → rút gọn → tạo giọng → căn thời gian → che chữ gốc.
- **Góc trên phải: Xuất CapCut / Xuất video.**

## Kết quả khi xuất sang CapCut

![Dự án CapCut do tool xuất](docs/ket-qua-capcut.webp)

Bấm **Xuất CapCut**, tool tạo sẵn một dự án và mở CapCut. Timeline đã chia thành các hàng:

- **Phụ đề khớp** (hàng trên cùng): phụ đề tiếng Việt đúng font, màu, vị trí đã chọn trong tool. Mỗi chữ có thời gian riêng, nên dùng được các mẫu chữ hiện từng chữ của CapCut (như "Quick").
- **Mờ chữ · mặt nạ:** các lớp che phụ đề gốc của video, chỉ xuất hiện lúc có chữ và nằm gọn trên một hàng.
- **Video gốc:** video được cắt thành các đoạn. Đoạn nào lời đọc dài hơn lời gốc thì được làm chậm vừa đủ (biểu tượng tốc độ trên clip).
- **Voice:** từng câu lồng tiếng, đặt đúng chỗ.

Mọi thứ vẫn chỉnh được trong CapCut như dự án bình thường: đổi chữ, đổi giọng, thêm hiệu ứng, nhạc nền rồi xuất video.

## Tool làm được gì

**Bóc phụ đề từ video**
- Nghe được tiếng Trung, Anh, Nhật, Hàn, Việt, hoặc để tool tự nhận ra ngôn ngữ.
- Nhận dạng bằng CapCut: các mẩu chữ ngắn được Gemini ghép lại thành câu trọn ý.
- Đã có phụ đề sẵn thì nhập file SRT/VTT.

**Dịch bằng AI**
- Dịch sang tiếng Việt hoặc tiếng Anh bằng Gemini. Có nhiều API key thì tool tự đổi key khi một key lỗi.
- Phong cách dịch có hướng dẫn xưng hô riêng cho từng thể loại phim.
- Câu nào Gemini bỏ sót thì tool tự dịch lại.

**Lồng tiếng Việt**
- Nhiều giọng nam, nữ, nghe thử trước khi dùng.
- Giọng VieNeu chạy ngay trên máy: nhanh, không cần mạng, đọc nhiều câu cùng lúc.
- Lồng tiếng theo nhân vật: tự nhận ra nhân vật và gán giọng.
- Tự chỉnh tốc độ đọc và rút gọn câu dài để lời đọc khớp với video.

**Phụ đề và che chữ gốc**
- Chỉnh font, cỡ chữ, màu, viền, nền, vị trí.
- Che phụ đề gốc có sẵn trong video: tool tự tìm vùng chữ và chỉ che lúc có chữ. Có nút Dò thử để xem trước.

**Làm nhiều video một lúc**
- Thêm nhiều video, bấm Dịch tất cả, rồi Xuất tất cả sang CapCut hoặc ra video.
- Chuột phải vào video → Gửi đến → Lồng tiếng CapCut: tool tự làm hết và mở CapCut.

## Giá
- Đăng ký miễn phí, dùng thử 1 ngày.
- Gói Pro: **190.000đ / 30 ngày**, thanh toán bằng mã QR ngay trong tool.

Hỗ trợ: **Zalo 0937659552**
