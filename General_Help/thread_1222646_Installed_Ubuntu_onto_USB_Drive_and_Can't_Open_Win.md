---
title: "Installed Ubuntu onto USB Drive and Can't Open Windows XP Now"
date: 2009-07-25
forum: General Help
---

### Post by flashice on 2009-07-25
Hello

I recently installed Ubuntu (8.10) onto a USB Drive. However now I can't load up XP, which is on the main hard drive of the computer, without the USB Drive attached. When I have the USB Drive attached, it brings up a menu asking which disk I want to boot from. If the USB Drive is not attached, then it say I have a Grub Error 21, and I cannot do anything but restart. I have checked the system settings and the computer is set to load from the hard drive, only it doesn't. Any help would be great. Thanks.

---

### Post by mikewhatever on 2009-07-25
You'll need to restore the Windows boot loader. If you don't have the cd, there are other way. Just google it.
[http://www.neowin.net/forum/lofiversion/index.php/t292614.html](http://www.neowin.net/forum/lofiversion/index.php/t292614.html)

The problem with the Windows boot loader is, it supports nothing else, but Windows. Doing the above will make your Ubuntu unbootable, and you'll need to reinstall GRUB, the Ubuntu boot loader too.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)

---

### Post by flashice on 2009-07-26
Thank you!! Worked!
:D

---

