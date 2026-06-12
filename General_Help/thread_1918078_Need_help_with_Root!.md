---
title: "Need help with Root!"
date: 2012-01-31
forum: General Help
---

### Post by tertian on 2012-01-31
Hello. I am a very new and inexperienced ubuntu/linux user (second day using it). I am currently just installing things and personalizing the OS with mouse gestures, finding the correct apps for me, getting to know the OS etc. 

The problem is, i want to paste a skin for Audacious in /usr/share/audacious/skins, but the whole '/' partition (i find it under 'File System', it's where i installed Ubuntu) is has owner:root and group:root. So i can't paste anything in '/', (the filesystem partition) nor create any folder or do anything at all. I read some stickies about the perils of Root and how one must not take it lightly, so i'd like some illumination on how i can manage to gain the temporary right to paste my skin in that damn folder, or how to gain temporary right to do such things, because i'll propably need to do something similar in the future. 

Thanks in advance

---

### Post by nothingspecial on 2012-01-31
Hi

Press Alt-F2 and type ```
gksudo nautilus
``` to open your file browser as root. Type your password.

Paste the file into the folder, then close the file browser.

---

### Post by tertian on 2012-01-31
hrm, just did it, thanks a lot! also fast reply :)

---

### Post by nothingspecial on 2012-01-31
No problem. Next time your issue is solved you can mark your thread Solved using the thread tools link at the top.

I've done it for you this time :)

---

