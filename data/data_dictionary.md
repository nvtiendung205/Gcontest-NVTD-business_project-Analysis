# Data Dictionary - GCONTEST Retail & Wholesale P&L Dataset

Tài liệu mô tả chi tiết 36 trường dữ liệu trong tập dữ liệu Báo cáo Kết quả Hoạt động Kinh doanh (P&L) của chuỗi thời trang đa kênh (75 cửa hàng, 13 chi nhánh, 3 miền Bắc - Trung - Nam) trong Quý 1 các năm 2022 và 2023.

---

## 1. Nhóm Định danh & Phân loại (Dimensions & Categorical Attributes)

| Tên trường (Column Name) | Kiểu dữ liệu | Diễn giải ý nghĩa | Giá trị mẫu / Định dạng |
| :--- | :---: | :--- | :--- |
| `KHU VỰC` | String | Khu vực địa lý của chi nhánh/cửa hàng | `MIỀN BẮC`, `MIỀN TRUNG`, `MIỀN NAM` |
| `CHI NHÁNH` | String | Tên chi nhánh quản lý trực tiếp các điểm bán | `Hà Nội`, `CN Hồ Chí Minh`, `CN Đà Nẵng`, `CN Cần Thơ`,... (13 chi nhánh) |
| `Mã TT` | Integer | Mã định danh duy nhất của từng trung tâm / cửa hàng (Store ID) | `101101`, `101102`, `311101`,... (75 mã cửa hàng) |
| `Tháng` | Integer | Tháng phát sinh số liệu kinh doanh | `1`, `2`, `3` |
| `NĂM` | Integer | Năm tài chính ghi nhận | `2022`, `2023` |
| `Quý` | Integer | Quý kế toán | `1` |
| `Mảng KD` | String | Dòng danh mục sản phẩm thời trang kinh doanh | `Thời trang nam`, `Thời trang nữ`, `Phụ kiện`, `Thời trang Unisex` |
| `Hình thức bán hàng` | String | Phương thức và kênh phân phối | `BÁN SỈ` (Wholesale), `BÁN LẺ` (Retail) |

---

## 2. Nhóm Doanh thu (Revenue Metrics)

| Tên trường | Kiểu dữ liệu | Diễn giải ý nghĩa | Công thức / Mối liên hệ |
| :--- | :---: | :--- | :--- |
| `Tổng Doanh thu` | Float (VND) | Tổng giá trị bán hàng phát sinh gộp | Doanh số trước khi trừ các khoản giảm trừ |
| `Các khoản giảm trừ DT` | Float (VND) | Chiết khấu thương mại, giảm giá bán hàng, hàng bán bị trả lại | `Tổng Doanh thu - Doanh thu thuần` |
| `Doanh thu thuần` | Float (VND) | Doanh thu thực tế sau khi đã trừ đi các khoản giảm trừ | `Doanh thu thuần = Tổng Doanh thu - Các khoản giảm trừ DT` |
| `Kế hoạch DTT` | Float (VND) | Chỉ tiêu Doanh thu thuần được giao theo ngân sách đầu kỳ | Target Benchmark để đánh giá hiệu quả kinh doanh |

---

## 3. Nhóm Chi phí Vận hành & Giá vốn (COGS & OPEX Metrics)

| Tên trường | Kiểu dữ liệu | Diễn giải ý nghĩa | Bản chất chi phí |
| :--- | :---: | :--- | :--- |
| `Giá vốn` | Float (VND) | Giá vốn hàng bán (Cost of Goods Sold - COGS) | Biến phí (Variable Cost) theo sản lượng tiêu thụ |
| `Chi phí bán hàng` | Float (VND) | Tổng chi phí phục vụ hoạt động bán hàng tại điểm bán | Tổng hợp các khoản chi phí trực tiếp bán hàng |
| `% chi phí` | Float (%) | Tỷ lệ chi phí bán hàng trên Doanh thu thuần | `Chi phí bán hàng / Doanh thu thuần` |
| `Thuê nhà, CP địa điểm` | Float (VND) | Tiền thuê mặt bằng, cửa hàng, kho bãi | Định phí cố định (Fixed Cost) |
| `Khấu hao TSCĐ` | Float (VND) | Chi phí khấu hao tài sản cố định, trang thiết bị quầy kệ | Định phí cố định (Fixed Cost) |
| `Lương +Ăn ca + Các khoản trích theo lương` | Float (VND) | Chi phí nhân sự cố định (lương cứng, bảo hiểm, ăn ca) | Định phí / Bán biến phí nhân sự |
| `Thưởng các loại` | Float (VND) | Thưởng hiệu quả kinh doanh, doanh số cho nhân viên | Biến phí gắn liền với kết quả kinh doanh |
| `Chi phí marketing` | Float (VND) | Ngân sách quảng cáo, tiếp thị, khuyến mãi thúc đẩy doanh số | Chi phí đầu tư tăng trưởng (Discretionary OPEX) |
| `Thuế (GTGT+ TTDB)` | Float (VND) | Thuế giá trị gia tăng và tiêu thụ đặc biệt phát sinh | Chi phí nghĩa vụ thuế gián thu |
| `Các khoản chi phí chung` | Float (VND) | Chi phí điện nước, văn phòng phẩm, vật tư tiêu hao cửa hàng | Chi phí vận hành cơ sở (Operating Expenses) |
| `Chi phí quản lý (phân bổ)`| Float (VND) | Chi phí quản lý doanh nghiệp cấp hội sở phân bổ về cửa hàng | Chi phí gián tiếp phân bổ (Allocated SG&A) |

---

## 4. Nhóm Lợi nhuận (Profitability Metrics)

| Tên trường | Kiểu dữ liệu | Diễn giải ý nghĩa | Công thức tính toán P&L |
| :--- | :---: | :--- | :--- |
| `Lợi nhuận gộp` | Float (VND) | Lãi gộp từ hoạt động bán sản phẩm | `Lợi nhuận gộp = Doanh thu thuần - Giá vốn` |
| `Lợi nhuận thuần từ HĐKD`| Float (VND) | Lợi nhuận từ hoạt động kinh doanh cốt lõi | `Lợi nhuận gộp - Chi phí bán hàng - Chi phí QLDN` |
| `Tổng lợi nhuận trước thuế`| Float (VND) | Tổng thu nhập trước khi trích nộp thuế TNDN (EBT) | `Lợi nhuận thuần HĐKD + LN hoạt động tài chính + LN khác` |
| `Chi phí thuế TNDN` | Float (VND) | Chi phí thuế thu nhập doanh nghiệp phát sinh | Thuế suất theo luật thuế TNDN hiện hành |
| `Lợi nhuận sau thuế` | Float (VND) | Lợi nhuận kế toán sau khi trừ thuế TNDN | `Tổng lợi nhuận trước thuế - Chi phí thuế TNDN` |
| `Lợi nhuận NET` | Float (VND) | Lợi nhuận ròng thực tế ghi nhận sau phân bổ | Chỉ số đo lường hiệu quả sinh lời ròng cuối cùng của điểm bán |
| `Kế hoạch LNN` | Float (VND) | Chỉ tiêu Lợi nhuận NET mục tiêu được giao trong kế hoạch | Target Benchmark để đánh giá tỷ lệ hoàn thành KPI |

---

## 5. Nhóm Hoạt động Tài chính & Khác (Non-operating & Financial Items)

| Tên trường | Kiểu dữ liệu | Diễn giải ý nghĩa |
| :--- | :---: | :--- |
| `Doanh thu hoạt động tài chính` | Float (VND) | Lãi tiền gửi, chiết khấu thanh toán nhận được |
| `Chi phí hoạt động tài chính` | Float (VND) | Lãi vay ngân hàng, phí chuyển tiền tài khoản |
| `Lợi nhuận thuần từ HĐTC` | Float (VND) | `Doanh thu HĐTC - Chi phí HĐTC` |
| `Thu nhập khác` | Float (VND) | Thanh lý tài sản, nhượng bán phế liệu, thu hồi công nợ khó đòi |
| `Chi phí khác` | Float (VND) | Các khoản phạt vi phạm hợp đồng, tổn thất ngoài kinh doanh |
| `Lợi nhuận khác` | Float (VND) | `Thu nhập khác - Chi phí khác` |

