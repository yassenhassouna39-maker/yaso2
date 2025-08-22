# Flashr — Website + Android App (Capacitor)

## المحتويات
- web/index.html (تسجيل بالإيميل والموبايل + شهادات + لوحة مطوّر)
- web/manifest.json + service-worker.js (PWA)
- package.json + capacitor.config.json (تحويل لتطبيق أندرويد)

## قبل التجربة
- Firebase Console → Authentication → فعّل Email/Password و Phone
- (اختياري) Phone test numbers لإرسال OTP للتجربة

## تشغيل كموقع
- افتح web/index.html في المتصفح أو شغّل Live Server من VS Code

## نشر على Firebase Hosting (مختصر)
1) npm i -g firebase-tools
2) firebase login
3) firebase init hosting  (اختر web كـ public، و SPA = Yes)
4) firebase deploy

## تحويل لتطبيق أندرويد (Capacitor)
1) npm i
2) npm run cap:add:android
3) npm run cap:sync
4) npm run cap:open:android  ← افتح Android Studio وابنِ APK

## Firestore قواعد مؤقتة (للتجربة فقط)
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.time < timestamp.date(2026,1,1);
    }
  }
}
```
> غيّر القواعد قبل الإطلاق.

## ملاحظات
- لوحة المطوّر تظهر فقط للحساب: yassenhassouna39@gmail.com
- كل مستخدم جديد يُحفظ في users (email/phone + وقت الإنشاء)
- الكورسات من collection اسمها courses
