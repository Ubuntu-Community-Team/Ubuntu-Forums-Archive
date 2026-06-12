---
title: "Can't find file-roller in xubuntu applications menu!"
date: 2011-06-03
forum: General Help
---

### Post by Defrector on 2011-06-03
:o I can't, for the life of me, find file-roller (aka 'Archive Manager') in xubuntu's Applications menu. I surely have it; it is the default application for opening archives, I can invoke it from the terminal but I can't just... run it from the Applications drop-down.

I even tried the Application Finder with no luck using the keywords file-roller, archive, file, roller, .zip. .tar, etc. No luck.

Can anyone else find it on their Applications dropdown menu? Or at least tell me that they can't find it either?

I'm curious if I have some configuration glitch, or if this is a bug, or maybe there's just something in the water here.

---

### Post by Toz on 2011-06-03
By default, it's not displayed. To display it in the menu, edit the file /usr/share/applications/file-roller.desktop (as root):```
sudo mousepad /usr/share/applications/file-roller.desktop
``` and change the line:```
NoDisplay=true
``` to read:```
NoDisplay=false
```

---

### Post by irv on 2011-06-06
Thank for the post Toz, I used it to make file-roller (Archive manager) show up in Accessories. Defrector why don't you mark this one solved.

---

