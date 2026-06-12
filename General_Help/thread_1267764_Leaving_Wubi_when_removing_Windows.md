---
title: "Leaving Wubi when removing Windows"
date: 2009-09-16
forum: General Help
---

### Post by matshofman on 2009-09-16
Hi,

I installed Wubi Ubuntu but i'm planning to remove windows vista from my laptop but does Wubi stay on my computer. I have installed Wubi on a difrent partiotion than windows.

Greetings,

Mats Hofman

---

### Post by rocket16 on 2009-09-16
I don't think Wubi will remain. This is because the BCD.exe bootloader will also beremovd. But, although not sure, you may copy the Bootloader folder (i.e BCD folder) to a CD or Drive, and replace the one of your new Installation. May be this works.

---

### Post by earthpigg on 2009-09-16
your ubuntu install, in this case, will not remain.

however, you can keep all your personal settings for programs by backing up your /home directory, installing ubuntu normally (this time, replacing windows), then restoring that /home directory onto the new ubuntu install. 

log out/back in for changes to take affect.

---

