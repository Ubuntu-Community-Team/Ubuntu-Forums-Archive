---
title: "Kino crashes"
date: 2006-03-28
forum: General Help
---

### Post by Lary Grant on 2006-03-28
Kino crashes every time I try to export an AVI file.  Capturing and exporting MPEG work fine.

---

### Post by claydoh on 2006-03-28
Check and see if ffmpeg is installed, it is needed to encode to avi. If it still crashes, try running Kino from a terminal to see any errors that appear.

---

### Post by Lary Grant on 2006-03-29
I get:

*** glibc detected *** double free or corruption (!prev): 0x08bb4368 ***

---

### Post by Lary Grant on 2006-03-29
I forgot to mention... I do have ffmpeg

---

### Post by fsman on 2006-03-29
do you have backports? If so, don't use the backport version - it crashes. Use the lock function in symantic to keep with the standard 0.7 build.

---

### Post by Lary Grant on 2006-03-29
No backports

---

### Post by _obelix_ on 2006-04-04
Sorry, my posting is wrong here.

Regards

Obelix

---

