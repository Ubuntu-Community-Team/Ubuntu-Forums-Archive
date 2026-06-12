---
title: "zenity wget"
date: 2010-07-20
forum: General Help
---

### Post by sandyd on 2010-07-20
hey, can someone crape up a zenity progress dialog with wget download progress please?

thanks!

---

### Post by sisco311 on 2010-07-21
```
wget --progress=bar:force "$URL" -O"$FILENAME" 2>&1 | zenity --title="$TITLE" --progress
```

---

