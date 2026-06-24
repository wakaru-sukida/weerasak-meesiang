# Weerasak Meesiang — Portfolio / วีรศักดิ์ มีเสียง — พอร์ตโฟลิโอ

เว็บพอร์ตโฟลิโอส่วนตัวแบบ 2 ภาษา (ไทย/อังกฤษ) ที่ดึงข้อมูลผลงานและประวัติแบบเรียลไทม์จาก **Google Sheet** — แก้ข้อมูลในชีต หน้าเว็บอัปเดตทันทีโดยไม่ต้อง deploy ใหม่

A bilingual (TH/EN) personal portfolio web app that pulls project and résumé data **live from a Google Sheet** — edit the sheet and the site updates instantly, no redeploy needed.

**🔗 Live demo:** https://wakaru-sukida.github.io/weerasak-meesiang/

---

## ✨ Features / ความสามารถ

- 🌐 **สองภาษา (TH/EN)** — สลับภาษาได้ทันที
- 🌗 **โหมดมืด/สว่าง** + เลือกโทนสีหลักได้ 5 สี
- 📁 **แท็บผลงาน (Work)** — กรองตามหมวดหมู่, จัดเรียง (ลำดับ/วันที่/หมวด), กริดการ์ด, แผงรายละเอียดแบบ drawer
- 👤 **แท็บเกี่ยวกับ (About)** — ข้อมูลส่วนตัว ประสบการณ์ การศึกษา ทักษะ กิจกรรม/งานวิจัย และบุคคลอ้างอิง
- 📄 **ดาวน์โหลดเรซูเม่เป็น PDF** สร้างฝั่งเบราว์เซอร์ (รองรับการเรนเดอร์ฟอนต์ไทยผ่าน canvas)
- 📊 **เชื่อมต่อ Google Sheet** ผ่าน gviz API — หากต่อไม่ได้จะแสดงข้อมูลตัวอย่างแทน
- 📱 **Responsive** รองรับมือถือ แท็บเล็ต และเดสก์ท็อป

## 🧱 Tech / เทคโนโลยี

- Claude Design Component (`.dc.html`) + DC runtime (`support.js`) ที่โหลด **React 18** อัตโนมัติ
- **jsPDF** สำหรับสร้างไฟล์ PDF (โหลดจาก CDN เมื่อกดดาวน์โหลด)
- ข้อมูลจาก **Google Sheets gviz JSON API** — ไม่ต้องมี backend

## 📂 Project structure / โครงสร้างไฟล์

```
.
├── index.html            # หน้าเริ่มต้น (สำเนาของ Portfolio.dc.html) สำหรับ hosting
├── Portfolio.dc.html     # คอมโพเนนต์หลัก: template + logic
├── support.js            # DC runtime (โหลด React + boot คอมโพเนนต์)
├── assets/
│   └── profile.png       # รูปโปรไฟล์ (ใช้เป็น fallback)
├── work_template.csv     # เทมเพลตคอลัมน์สำหรับชีต "Work"
├── about_template.csv    # เทมเพลตคอลัมน์สำหรับชีต "About"
└── .nojekyll             # ปิด Jekyll บน GitHub Pages (เสิร์ฟไฟล์ตามจริง)
```

## ▶️ Run locally / รันในเครื่อง

ต้องเปิดผ่าน web server (ไม่ใช่ double-click ไฟล์ เพราะการ `fetch` Google Sheet จะถูก CORS บล็อกบน `file://`):

```bash
python -m http.server 8000
# แล้วเปิด http://localhost:8000/
```

## 📊 Editing content / แก้ไขเนื้อหา

ข้อมูลทั้งหมดมาจาก Google Sheet (กำหนดด้วย `sheetId` ในไฟล์ `Portfolio.dc.html`)

- ชีต **Work** — ผลงานแต่ละชิ้น (ดูคอลัมน์ใน [`work_template.csv`](work_template.csv))
- ชีต **About** — ประวัติ/เรซูเม่ (ดูคอลัมน์ใน [`about_template.csv`](about_template.csv))

คอลัมน์รองรับทั้งหัวข้อภาษาไทยและอังกฤษ ระบบจะจับคู่คอลัมน์ให้อัตโนมัติ

## 🚀 Deploy / การ deploy

โฮสต์เป็น static site ได้ทุกที่ (GitHub Pages, Netlify, Vercel ฯลฯ) — สำหรับ GitHub Pages:

```bash
git add -A
git commit -m "update"
git push
```

แล้วเปิด **Settings → Pages → Deploy from a branch → `main` / root**

---

© Weerasak Meesiang (Mac)
