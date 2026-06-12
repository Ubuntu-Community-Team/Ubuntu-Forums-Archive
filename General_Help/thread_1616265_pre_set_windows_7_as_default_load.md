---
title: "pre set windows 7 as default load"
date: 2010-11-08
forum: General Help
---

### Post by reinaldistic on 2010-11-08
i just reinstalled linux on partition (ubuntu) and i remember last time i did it i was able to set windows as default load and with a timer so that after 3 seconds windows would load and not ubuntu

default right now is ubuntu load after 10 seconds...
please help

---

### Post by Quackers on 2010-11-08
Everything you need is in here

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by bibble235 on 2010-11-08
set default="0"

from /boot/grub/grub.cfg controls which is booted first.

grep menuen /boot/grub/grub.cfg will show you your entries.

---

### Post by Jahid65 on 2010-11-08
Install startup manager. It has the option you looking for.

---

