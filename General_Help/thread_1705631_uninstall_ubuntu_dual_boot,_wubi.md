---
title: "uninstall ubuntu dual boot, wubi"
date: 2011-03-12
forum: General Help
---

### Post by weybrew on 2011-03-12
I originally installed Ubuntu via Wubi (dual boot with Win 7, 32). I now want to uninstall and I thought going through the Wubi install procedure again would switch Wubi to an uninstaller but that hasn't worked. How can I uninstall Ubuntu?

---

### Post by andrewthomas on 2011-03-12
[https://help.ubuntu.com/community/Wubi#Windows-based%20Un-installation](https://help.ubuntu.com/community/Wubi#Windows-based%20Un-installation)

---

### Post by Rubi1200 on 2011-03-12
Also here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

see the instructions for manual uninstall if the regular method does not work for some reason.

---

### Post by weybrew on 2011-03-12
Thanks to andrewthomas...Good idea except Ubuntu isn't listed in the list of installed programs. It does appear in the boot window as an OS choice.

---

### Post by weybrew on 2011-03-12
Thanks to Ribi1200...Will try the manual uninstall, the auto doesnt' help. Ubuntu doesn't appear on my program install/uninstall list but it does appear as a boot option on Restart.

---

### Post by wilee-nilee on 2011-03-12
> **weybrew said:**
> Thanks to Ribi1200...Will try the manual uninstall, the auto doesnt' help. Ubuntu doesn't appear on my program install/uninstall list but it does appear as a boot option on Restart.

There is a uninstall button in the Ubuntu file, if you haven't already removed anything. You have to be in admin to do any of this I believe as well.

---

### Post by weybrew on 2011-03-13
Thanks, wilee-nilee. Found it, tried it, no change.

---

### Post by weybrew on 2011-03-13
Thanks to all. Have tried suggested remedies without success. Ubuntu still shows on boot window as OS choice, BUT....selecting Ubuntu gives "...no wubibldr" note and ERROR: Can't find GRLDR...
I have done a file search and find files per attached screen shots. What happens if I just manually delete all shown files?

---

### Post by bcbc on 2011-03-13
Looks like wubi-uninstall.exe is missing. Stick in the CD again and run wubi. It should remove the old install. Then it will either exit or prompt to reinstall - just cancel that.

Otherwise follow the manual uninstall instructions that Rubi1200 linked to.

---

### Post by weybrew on 2011-03-14
Thanks for the replies... the problem appears to have been leftover information. Easy BCD program removed unwanted Ubuntu boot selection and deleting the previously used partition cleaned things up. 

RESOLVED

---

### Post by Rubi1200 on 2011-03-14
Glad you got things sorted out in the end.

---

