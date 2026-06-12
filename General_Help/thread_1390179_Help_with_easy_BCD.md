---
title: "Help with easy BCD"
date: 2010-01-25
forum: General Help
---

### Post by tesseract4d on 2010-01-25
I just dual booted my machine which initially had windows 7 to a 7 + ubuntu machine. I've installed easyBCD to facilitate the chosing when the system starts up but I don't really know the code to write in the configuration.

Every time I start up I'm given 2 options 1. Windows 7 or 2. Neo Grub Boot loader but the 2nd one doesn't work.

Any help

---

### Post by tim15856 on 2010-01-25
You should also see a Linux/grub option. I just tried it yesterday, but couldn't get Ubuntu to boot. I have to search around to see what to try. If I find a solution, I'll post it here.

---

### Post by tim15856 on 2010-01-27
The fix is to use the latest beta version of easyBCD, I used beta 2.0 build 76. You have to register on their forum, then you can download it from here. [http://neosmart.net/forums](http://neosmart.net/forums) Select the Linux tab, change the name if you wish. Use the 'grub legacy' option and check the box 'grub isn't on mbr' (or something like that). Then hit the 'add' button. If the order is OK, then select 'save' at the top.

---

