---
title: "typing the letter &quot;e&quot; in terminal acts like &quot;paste&quot;"
date: 2009-08-18
forum: General Help
---

### Post by alienclone on 2009-08-18
all of a sudden when i type the letter "e" in a terminal console (works fine anywhere else), it will paste whatever is in my clipboard instead of the actual letter "e". the only way i can put an actual "e" in the terminal is by using caps lock then "shift+e", or copy and paste it in.
its becoming a pain especially since there are "e"s in my password.  i musta hit some hotkey combo that activated it somehow but dont know what i did or how to fix it.

---

### Post by geirha on 2009-08-18
Hit alt+f2 and run «gconf-editor». In gconf-editor, browse to /apps/gnome-terminal/keybindings/.  What is «paste» set to? (<Ctrl><Shift>v is the default)

---

### Post by alienclone on 2009-08-18
I love you sooo much, thankyou for the quick reply and thorough walkthru.

---

### Post by randumnumber on 2010-01-30
Baaaad aaaasssss, i didn't have this problem but, now i know how to assign key combos ill be short cutting my way everywhere.

---

