# حل مشكلة تعارض الـ Pull Request (index.html)

لو ظهر لك في GitHub: **This branch has conflicts that must be resolved**

## السبب
- ملف `index.html` اتعدل في `main` وفي فرعك في نفس الأماكن.
- GitHub مش قادر يدمج تلقائيًا.

## الحل السريع (سطر أوامر)

> نفّذ الأوامر من نفس الريبو المحلي

```bash
git fetch origin
git checkout <your-branch>
git merge origin/main
```

لو ظهر تعارض في `index.html`:

```bash
git checkout --ours index.html
# أو لو عايز نسخة main:
# git checkout --theirs index.html

git add index.html
git commit -m "Resolve merge conflict in index.html"
git push origin <your-branch>
```

## حل أفضل (موصى به)
- افتح `index.html` يدويًا بعد `git merge origin/main`.
- اجمع بين التعديلات المطلوبة من الفرعين بدل اختيار نسخة واحدة بالكامل.
- ثم:

```bash
git add index.html
git commit -m "Resolve merge conflict and keep both updates"
git push origin <your-branch>
```

## ملاحظة
- بعد الـ push هتختفي رسالة التعارض في صفحة الـ PR تلقائيًا.
