# مساعد أولياء أمور ثانوية بحرة الأولى

نسخة جاهزة للاستضافة على GitHub Pages مع Supabase.

## الملفات
- `index.html` الموقع العام لأولياء الأمور.
- `admin/index.html` لوحة الإدارة الخاصة.
- `supabase-config.js` بيانات مشروع Supabase.
- `supabase-schema.sql` إنشاء الجداول والصلاحيات.

## 1) إنشاء مشروع Supabase
1. افتحي https://supabase.com وأنشئي مشروعًا.
2. من SQL Editor شغّلي محتوى `supabase-schema.sql`.
3. من Authentication > Users أنشئي حساب الإدارة بالبريد الإلكتروني وكلمة المرور.
4. انسخي User UID للحساب.
5. في SQL Editor شغّلي:
   `insert into public.admins (user_id) values ('ضعي-UID-هنا');`
6. من Project Settings > API انسخي Project URL و anon public key إلى `supabase-config.js`.

مهم: لا تضعي `service_role` key في المشروع أو GitHub.

## 2) GitHub Pages
ارفعي الملفات إلى مستودع GitHub:
- index.html
- supabase-config.js
- supabase-schema.sql
- admin/index.html

ثم:
Settings > Pages > Deploy from a branch > main > /(root)

بعد النشر:
- الموقع العام: `https://USERNAME.github.io/REPOSITORY/`
- لوحة الإدارة: `https://USERNAME.github.io/REPOSITORY/admin/`

## الأمان
مفتاح Supabase anon يمكن أن يكون في الواجهة، لأن الحماية الفعلية تأتي من Row Level Security في قاعدة البيانات.
صلاحيات الإضافة والتعديل والحذف مقيدة بحساب موجود في جدول `admins`.
لا تضعي كلمة مرور أو service_role key داخل ملفات GitHub.
