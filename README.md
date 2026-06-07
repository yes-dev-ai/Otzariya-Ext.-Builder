<div align="center">

# 📦 Otzaria Plugin Studio 🚀

### סביבת פיתוח, אריזה והפצה לתוספי [אוצריא](https://github.com/Sivan22/otzaria)

*כתבת תוסף ב-HTML? יופי. מכאן והלאה — אנחנו דואגים לכל ה"מסביב" כדי שתחזור ללמוד.*

[![Open Studio](https://img.shields.io/badge/🚀_פתח_את_הסטודיו-online-blue?style=for-the-badge)](https://y-ploni.github.io/Otzaria-Plugins-fast/)
[![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](#)
[![Made for Otzaria](https://img.shields.io/badge/made_for-Otzaria-indigo?style=for-the-badge)](https://github.com/Sivan22/otzaria)

</div>

---

## 📑 תוכן עניינים

- [על מה מדובר?](#-על-מה-מדובר)
- [למה צריך את זה?](#-למה-צריך-את-זה)
- [מה הסטודיו עושה בשבילך](#-מה-הסטודיו-עושה-בשבילך)
- [איך זה עובד — תהליך אריזה ב-3 שלבים](#-איך-זה-עובד--תהליך-אריזה-ב-3-שלבים)
- [אנטומיה של קובץ `.otzplugin`](#-אנטומיה-של-קובץ-otzplugin)
- [מערכת ההרשאות](#-מערכת-ההרשאות)
- [שילוב עם Otzaria SDK](#-שילוב-עם-otzaria-sdk)
- [תמיכה ב-Offline](#-תמיכה-ב-offline)
- [קבצים נוספים, גופנים ואייקונים](#-קבצים-נוספים-גופנים-ואייקונים)
- [טיפים והמלצות](#-טיפים-והמלצות)
- [שאלות נפוצות](#-שאלות-נפוצות)
- [תרומה לפרויקט](#-תרומה-לפרויקט)
- [Buy me a coffee](#-ולסיום--buy-me-a-coffee)

---

## 💡 על מה מדובר?

**Otzaria Plugin Studio** הוא כלי גרפי (web-based, ללא התקנה) שהופך עמוד HTML בודד לתוסף מלא ופועל לאפליקציית **אוצריא** — בלי לחשוב על מבנה תיקיות, מניפסטים, JSON, הרשאות, או על איך לעטוף סקריפטים מרוחקים.

הכל קורה בדפדפן שלך. שום קוד לא נשלח לשרת — הכל לוקאלי, מהיר ופרטי.

> **TL;DR:** זרוק HTML, מלא טופס, קבל קובץ `.otzplugin` מוכן להתקנה.

---

## 🤔 למה צריך את זה?

תוסף תקני לאוצריא הוא ארכיון `.zip` (בסיומת `.otzplugin`) שמכיל לפחות:

```
your-plugin.otzplugin
├── manifest.json        ← מטא-דאטה: שם, ID, גרסה, הרשאות, lifecycle
├── index.html           ← נקודת הכניסה של ה-WebView
└── otzaria_plugin.js    ← ה-bridge ל-API של ההוסט (אופציונלי — מוזרק אוטומטית)
```

לבנות את זה ידנית זה קצת כאב ראש: צריך לזכור את שמות השדות, להתאים גרסאות SemVer, לסמן את ההרשאות הנכונות, להוריד CDN-ים מקומית כדי שהתוסף יעבוד אופליין, להזריק קוד שמסנכרן עם מצב לילה...

**הסטודיו עושה את כל זה בשבילך.**

---

## ✨ מה הסטודיו עושה בשבילך

| תחום | מה קורה מאחורי הקלעים |
|---|---|
| 🧾 **יצירת מניפסט** | טופס ויזואלי לכל שדות `manifest.json` — שם, ID, גרסה, מחבר, dep ל-`minAppVersion`, רמת יציבות (`stable`/`beta`/`experimental`), ועוד. |
| 🔐 **בחירת הרשאות API** | רשימה ויזואלית של כל ה-permissions הנתמכים, מדורגת לקטגוריות, עם הסבר על כל אחת. סמן וזהו. |
| 🎨 **סנכרון Theme אוטומטי** | מזריק לתוסף קוד שמאזין לאירועי `plugin.boot` ו-`theme.changed` ומעדכן CSS variables — כך שהתוסף שלך מקבל **מצב לילה ב-0 שורות קוד**. |
| 📦 **Bundle Offline** | סורק את ה-HTML שלך, מאתר `<script src>` ו-`<link href>` חיצוניים, מוריד אותם, ומחליף ב-paths לוקאליים בתוך ה-ZIP. |
| 🆘 **Wizard למשאבים חסומים** | אם CDN חוסם הורדה דרך CORS — תפתח חלונית שמציעה לך לשמור את הקובץ ידנית ולהעלות אותו. |
| 📁 **קבצים נוספים** | גרור-ושחרר CSS, JS, TS, `.woff2`, תמונות וכל קובץ סטטי — כולם נארזים ב-root של ה-ZIP. |
| 🛠️ **עורך קוד מובנה** | textarea סגנון VSCode עם dark theme, טעינת קובץ מקומי, וטעינת תבנית "שלום עולם" מובנית. |
| 🏷️ **לשונית בתוך האפליקציה** | קביעת שם הלשונית, סדר ההופעה, ושם אייקון מתוך ספריית FluentUI System Icons (למשל `book_24_regular`). |
| 📡 **Published Data Types** | תמיכה בתוספים שמפרסמים אירועים לאפליקציה (`calendar.event`, `saved.query`, `note.draft` וכו'). |

---

## 🚀 איך זה עובד — תהליך אריזה ב-3 שלבים

### שלב 1: מלא את הטופס
- **שם** של התוסף (בעברית, איך הוא יופיע למשתמש)
- **מזהה ייחודי** — נוסחת `com.yourname.pluginid` (חובה — מזהה גלובלי)
- **גרסה** — SemVer (`1.0.0`)
- **גרסת אוצריא מינימלית** — `0.9.0` ומעלה
- **רמת יציבות** — `stable` / `beta` / `experimental`

### שלב 2: סמן הרשאות + טען HTML
- בחר רק את ההרשאות שהתוסף **באמת** צריך (משתמשים יראו אותן בעת התקנה)
- העלה את קובץ ה-HTML שלך, או התחל מתבנית "שלום עולם"
- הוסף קבצים נלווים (גופנים, CSS, סקריפטים מקומיים)

### שלב 3: לחץ "ארוז לתוסף"
- הסטודיו ייצור `manifest.json`, יזריק את `otzaria_plugin.js`, יוריד משאבים חיצוניים, ויפיק לך `.otzplugin` להורדה
- אם יש משאבים שחסומים בהורדה אוטומטית, יפתח wizard ויבקש אותם ידנית
- שניות לאחר מכן — קובץ אצלך, מוכן לגרירה לאוצריא

---

## 🧬 אנטומיה של קובץ `.otzplugin`

הקובץ הוא ZIP רגיל. שנה את הסיומת ל-`.zip` ותוכל לפתוח ולראות:

```jsonc
// manifest.json (מקוצר)
{
  "id": "com.myname.newplugin",
  "name": "תוסף חדש לאוצריא",
  "description": "תיאור התוסף החדש שלי.",
  "version": "1.0.0",
  "author": "Otzaria User",
  "homepage": "https://github.com/...",
  "stability": "beta",
  "minAppVersion": "0.9.0",
  "main": "index.html",
  "contributes": {
    "toolTab": {
      "title": "התוסף שלי",
      "iconName": "book_24_regular",   // שם אייקון FluentUI 24px (regular/filled)
      "order": 100
    }
  },
  "permissions": [
    "ui.feedback",
    "events.subscribe:theme.changed"
  ],
  "publishedDataTypes": []   // אופציונלי — אם התוסף מפרסם אירועים
}
```

---

## 🛡️ מערכת ההרשאות

הסטודיו מציג רשימה מלאה של ה-permissions הנתמכים. הם מתחלקים בגדול ל-3 משפחות:

### Direct calls (`.read` / `.write`)
| Permission | למה זה משמש |
|---|---|
| `library.read` | חיפוש ספרים, קריאת תוכן |
| `reader.open` / `reader.context_menu` | פתיחת ספרים בקורא, הוספת פריטים לתפריט קליק-ימני |
| `navigation.write` | ניווט אוטומטי בין מסכים |
| `notes.read` / `notes.write` | קריאה ועריכה של הערות אישיות |
| `calendar.read` | לוח שנה וזמני היום |
| `settings.read` | קריאת הגדרות אפליקציה |
| `history.read` / `history.write` | גישה להיסטוריית הלמידה |
| `database.read` | שאילתות מסד נתונים |
| `plugin.storage.read` / `plugin.storage.write` | אחסון מקומי לתוסף |
| `published_data.write` | פרסום אירועים לאפליקציה |
| `ui.feedback` | הצגת הודעות, סנאקבארים, דיאלוגים |
| `notifications.send` / `notifications.system` | פופאפים פנים-אפליקציה והתראות OS מתוזמנות |
| `feedback.send_email` | שליחת מייל משוב |
| `network.access` | גישה לאינטרנט (לתוספים שצריכים API חיצוני) |

### Event subscriptions (`events.subscribe:*`)
האזנה לאירועי המערכת:
- `theme.changed` — מצב יום/לילה השתנה
- `navigation.changed` — המשתמש עבר מסך
- `reader.current_book_changed` / `reader.current_ref_changed` / `reader.selection_changed` — מעקב אחר הקורא
- `calendar.date_changed` — שינוי תאריך בלוח
- `settings.changed` / `workspace.changed` / `plugin.permissions_changed`

> **כלל אצבע:** בקש רק מה שאתה משתמש בו בפועל. הרשאות מיותרות גורמות למשתמשים לחשוד.

---

## 🔌 שילוב עם Otzaria SDK

לאחר אריזה, התוסף שלך פועל בתוך WebView, ואוצריא מזריק אליו אובייקט גלובלי בשם `window.Otzaria`. ה-SDK תומך ב-3 פונקציות מרכזיות:

```js
// 1. קריאה ל-Host API
const { success, data, error } =
  await Otzaria.call('library.findBooks', { query: 'רמב"ם' });

// 2. הרשמה לאירוע
Otzaria.on('theme.changed', theme => applyTheme(theme));

// 3. הסרת מאזין
Otzaria.off('theme.changed', myHandler);
```

### אירועי lifecycle חשובים

| Event | Payload | מתי |
|---|---|---|
| `plugin.boot` | `{ plugin, app, theme, permissions }` | פעם אחת, מיד עם טעינה |
| `theme.changed` | `ThemePayload` | כשמשתמש מחליף בין יום/לילה |
| `plugin.permissions_changed` | `{ permissions: string[] }` | כשהרשאות התוסף השתנו |
| `reader.selection_changed` | סלקציה נוכחית | המשתמש בחר טקסט בקורא |

> בעת הזרקת ה-Boilerplate (toggle ראשון בסטודיו), הסטודיו מוסיף לך אוטומטית קוד שמסנכרן את ה-CSS Variables עם ערכי ה-theme של ההוסט — אז ה-`<body>` שלך מקבל מצב לילה בחינם.

---

## 🌐 תמיכה ב-Offline

ה-toggle "תמיכה עצמאית באופליין" עושה את הדבר הבא:

1. **סורק** את ה-HTML שלך אחרי `<script src="https://...">` ו-`<link rel="stylesheet" href="https://...">`.
2. **מנסה להוריד** כל URL חיצוני דרך `fetch()`.
3. אם ההורדה הצליחה — שומר את הקובץ ב-ZIP בשם נורמליזד (למשל `tailwind.js`) ומחליף את ה-src ב-path יחסי.
4. אם CORS חוסם — פותח את **Manual Upload Wizard**: לכל URL בעייתי תקבל לחצן "פתח את הקובץ", "שמור As..." ו"העלה לכאן". כך התוסף שלך נארז כיחידה עצמאית גם כשה-CDN לא משתף פעולה.

> תוצאה: התוסף שלך עובד גם בלי אינטרנט, גם אחרי שה-CDN ייעלם, ובלי תלות בעולם החיצון.

---

## 📂 קבצים נוספים, גופנים ואייקונים

הקלק על "הוסף קבצים" כדי לארוז לתוסף כל דבר נוסף:
- 🔤 **גופנים**: `.woff2`, `.ttf`, `.otf` — מומלץ [Rubik](https://fonts.google.com/specimen/Rubik?script=Hebr) לעברית
- 🎨 **CSS / Tailwind**: שמור Save-As את `cdn.tailwindcss.com` ל-`tailwind.js` להבטחת אופליין
- 🖼️ **תמונות / SVG**: [Heroicons](https://heroicons.com/), [Lucide](https://lucide.dev/)
- ⚙️ **JS / TS** — מודולים מקומיים שאתה רוצה לטעון

הקבצים נשמרים ב-root של ה-ZIP, וזמינים ל-`index.html` בנתיב יחסי:

```html
<link rel="stylesheet" href="rubik.css">
<script src="tailwind.js"></script>
<img src="logo.svg">
```

### אייקון לתוסף
שדה `contributes.toolTab.iconName` הוא **שם אייקון** מ-[FluentUI System Icons](https://github.com/microsoft/fluentui-system-icons) בגודל 24px. השם חייב להסתיים ב-`_24_regular` או `_24_filled`. דוגמאות: `book_24_regular`, `calendar_24_filled`, `search_24_regular`. אוצריא פותרת את השם למפת אייקונים סטטית פנימית — מה שמאפשר ל-Flutter לבצע tree-shaking נכון של פונט האייקונים ב-Release. שם שאינו מוכר יוצג כפאזל ברירת מחדל.

---

## 💡 טיפים והמלצות

### ✅ DO
- **השתמש ב-CSS Variables** של ה-theme — `--primary`, `--surface`, `--on-surface` — במקום צבעים קשיחים. כך התוסף שלך מסתנכרן אוטומטית עם מצב לילה.
- **בקש מינימום הרשאות.** משתמשים מודאגים יותר היום מתמיד.
- **בדוק SemVer.** עליית major תפעיל למשתמשים אזהרת תאימות.
- **הרץ את התוסף לוקאלית** באוצריא לפני פרסום (גרור את ה-`.otzplugin` ישירות לאפליקציה).

### ❌ DON'T
- **לא לקודד צבעים ישירות** (`background: #fff`) — תיהרסו במצב לילה.
- **לא להניח שיש אינטרנט.** אוצריא היא אפליקציית לימוד; משתמשים רבים בה offline.
- **לא לבקש `network.access`** אלא אם באמת צריך לתקשר עם שרת חיצוני.
- **לא לעקוף את ה-API** של ההוסט עם פתרונות יצירתיים — הם פשוט לא יעבדו.

---

## ❓ שאלות נפוצות

<details>
<summary><b>הסטודיו שולח את הקוד שלי לאיזשהו שרת?</b></summary>
לא. הכל רץ בדפדפן שלך, באופן מקומי לחלוטין. הקובץ שמופק יורד ישירות אליך — שום דבר לא עוזב את המכונה (פרט להורדת CDN-ים שאתה במפורש מאפשר ל-bundle).
</details>

<details>
<summary><b>למה ה-CDN לא נטען אוטומטית?</b></summary>
חלק מספקי CDN (כולל Google Fonts ו-Cloudflare מסוימים) חוסמים בקשות `fetch` ממקורות אחרים בגלל CORS. במקרה כזה הסטודיו פותח wizard ידני שמסביר איך להוריד את הקובץ ולהעלות אותו.
</details>

<details>
<summary><b>איך אני יודע איזו הרשאה לסמן?</b></summary>
התחל **בלי כלום**. הרץ את התוסף, ראה איזה <code>Otzaria.call(...)</code> מחזיר שגיאת permission, וסמן רק את מה שצריך.
</details>

<details>
<summary><b>אפשר להגיש PR לתבנית הברירת-מחדל?</b></summary>
בהחלט — ראה <a href="#-תרומה-לפרויקט">תרומה לפרויקט</a> מטה.
</details>

<details>
<summary><b>איך אני מתקין את ה-<code>.otzplugin</code> שיצרתי?</b></summary>
פתח את אוצריא → הגדרות → תוספים → גרור את הקובץ פנימה. או: לחץ "התקן מקובץ" ובחר את ה-<code>.otzplugin</code>.
</details>

---

## 🤝 תרומה לפרויקט

הסטודיו הוא קובץ HTML בודד (`index.html`) ללא bundler, ללא npm install. רוצה לעזור?

1. Fork את הריפו
2. ערוך את `index.html` ישירות (Tailwind via CDN, JSZip via CDN)
3. בדוק לוקאלית: `python3 -m http.server` ופתח `http://localhost:8000`
4. שלח PR

תחומים שמתבקשים תרומה:
- 🎯 הוספת permissions חדשים ככל שה-API של אוצריא מתרחב
- 🧪 בדיקות אינטגרציה אל מול ה-host
- 📚 דוגמאות תוספים (snippets) שאפשר לטעון מתוך הסטודיו
- 🌍 תרגומים ל-UI (כרגע עברית בלבד)

---

## ☕ ולסיום — Buy me a coffee

הכלי הזה פתוח לכולם בחינם, להגדיל תורה ולהאדירה.
אם חסכתי לך זמן — תכבד אותי בכוס קפה ובלימוד מתוך מנוחת הדעת.

[![support](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/shtaygen)

<div align="center">

---

**עשוי באהבה לקהילת אוצריא ❤️**

*לא משנה מה אתה בונה — תתחיל ב-`/קבצים נלווים → טען תבנית` ותראה איך זה עובד.*

</div>
