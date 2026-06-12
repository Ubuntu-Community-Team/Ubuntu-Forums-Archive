---
title: "Seems slower, longer purple screen"
date: 2011-10-06
forum: General Help
---

### Post by ernestj on 2011-10-06
It seems that when I boot up, it is taking longer than usual. Any suggestions? Thanks, Ernie

---

### Post by Frogs Hair on 2011-10-06
Are there any changes you have made including updates , settings , drivers , or programs ? Have you looked at the log file viewer ?

---

### Post by duke.tim on 2011-10-06
Basic maintenance  needed?

Try running fsck on reboot

```
cd /
sudo touch /forcefsck
```

Reboot to run


!!Don't do this until you follow what Frog Hair suggests!!
Clear your temporary files
(I really doubt this is causing it but it is worth a try)

download bleach bit and select

:Firefox:all

: Deep scan:
.Ds_Store
Temporary files
Thumbs.db

:System:
Cache
Clipboard
Temporary files
Trash

:Thumbnails
cache

---

