---
title: "Grub Error 15 Booting Issue"
date: 2010-05-01
forum: General Help
---

### Post by zachHH on 2010-05-01
After upgrading 9.10 to 10.04 last night, I was messing around with usplash themes using startup-manager. Not thinking, I accidentally set the default kernel to the one Ubuntu 9.10 uses, which I had already deleted. My only GRUB options are 9.10, 9.10 (recovery mode), and memory test, which all come up with Grub Error 15 (file not found). I cannot boot up into 10.04, and it's not even an option in GRUB. Is there any way I can reset GRUB or something? Please help!:(

Thanks!

EDIT: SOLVED! At the grub screen, I was able to edit the kernel on the lines from 2.6.31-20 to 2.6.32-21. Once I was booted, I uninstalled and reinstalled grub, and ran update-grub. Problem solved.

---

