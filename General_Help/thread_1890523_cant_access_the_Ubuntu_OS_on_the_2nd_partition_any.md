---
title: "cant access the Ubuntu OS on the 2nd partition anymore"
date: 2011-12-03
forum: General Help
---

### Post by electromagnetic on 2011-12-03
Hi there.

Some months ago , I installed Ubuntu on my second disk drive ( barely some 17gbs ). I used to get an option asking which operating system to boot from (windows 7 or Ubuntu) at the start up... But Now I dont get any such option, niether  i see the other partition in my Computer in Windows 7. can u please tell me how to get it back?

I am sure it is still installed there , I can see the partition using the Disk management tool.

---

### Post by deonis on 2011-12-03
Main question is what did you do to make it disappear? Do you see a grub menu or win7 just boot in ?

---

### Post by electromagnetic on 2011-12-03
> **deonis said:**
> Main question is what did you do to make it disappear? Do you see a grub menu or win7 just boot in ?
No , i donot see any grub menu. When ever i start my laptop, it boots up Windows 7 without asking.

---

### Post by deonis on 2011-12-03
It looks like you've killed the grub.  You will need to reinstall it. Please, follow this link:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by oldfred on 2011-12-03
Did you install grub to the second drive. And was this a second physical drive or windows speak for drives just another partition?

Post this from liveCD:

sudo fdisk -lu

---

