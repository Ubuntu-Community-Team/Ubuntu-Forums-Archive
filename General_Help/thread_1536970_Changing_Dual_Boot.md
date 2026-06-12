---
title: "Changing Dual Boot"
date: 2010-07-22
forum: General Help
---

### Post by scgp98 on 2010-07-22
First of all let me start off by saying that i am new here and hope that i post this in the right section' if not sorry

So my current setup is xp and unbuntu (dual boot) and i was wondering if there is anyway that i can get rid of xp and install Windows 7 instead and still be able to choose which one to boot from the grub at first boot?

---

### Post by ubunterooster on 2010-07-22
Install 7 then see the page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2010-07-22
If you want to directly boot from grub this will work. But then windows will not have both both loaders combined into the copy of windows with the boot flag.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

