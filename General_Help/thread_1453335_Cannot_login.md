---
title: "Cannot login"
date: 2010-04-13
forum: General Help
---

### Post by Kkatt on 2010-04-13
Hi,
After installing some new software (Digi Connect RealPort [http://ftp1.digi.com/support/documentation/90000630_D.pdf](http://ftp1.digi.com/support/documentation/90000630_D.pdf)) and switching off my computer I get a following error message at login:
> There is a problem with the configuration server usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256. After pressing OK I get to enter my password but then I am returned to the same error message and I can not log in.
I have searched the forum and found some posts with a similar problem but they mostly talk about ICEauthority and how to change permissions on it so they were not of much help. (My ICEauthority permissions seam to be OK).
Deinstalling the software didn't help.
I can log in at recovery mode but I am still quite new to linux and have no idea what to try.
I use ubuntu 9.10.
Any help will be greatly appreciated. 
Kat

---

### Post by Doctor Mike on 2010-04-13
> **Kkatt said:**
> Hi,
After installing some new software (Digi Connect RealPort [http://ftp1.digi.com/support/documentation/90000630_D.pdf](http://ftp1.digi.com/support/documentation/90000630_D.pdf)) and switching off my computer I get a following error message at login:
After pressing OK I get to enter my password but then I am returned to the same error message and I can not log in.
I have searched the forum and found some posts with a similar problem but they mostly talk about ICEauthority and how to change permissions on it so they were not of much help. (My ICEauthority permissions seam to be OK).
Deinstalling the software didn't help.
I can log in at recovery mode but I am still quite new to linux and have no idea what to try.
I use ubuntu 9.10.
Any help will be greatly appreciated. 
KatIs this: [http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)  what your looking for?

---

### Post by Kkatt on 2010-04-13
Fixed:
sudo apt-get --reinstall install ubuntu-desktop

---

