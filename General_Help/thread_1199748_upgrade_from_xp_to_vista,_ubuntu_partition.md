---
title: "upgrade from xp to vista, ubuntu partition?"
date: 2009-06-29
forum: General Help
---

### Post by medic0079 on 2009-06-29
just wondering if it is possible to upgrade from xp to vista, without messing with the ubuntu side of my hdd. 
I dual boot xp/jaunty, and wanted to know if I drop in the vista disk and do the upgrade to xp will it alter my jaunty partition, or is there no interaction? anyone done this before?
thanks!

---

### Post by nateperson on 2009-06-29
There will be no interaction between the partitions, so your data will not be affected. But a vista upgrade may try and put in a new bootloader, which will affect grub.

---

### Post by medic0079 on 2009-06-29
any suggustions what to do about that?

---

### Post by Greyfox_75 on 2009-06-29
After you install Vista and it overwrites grub grab a live cd and follow this 

[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by medic0079 on 2009-08-01
so tried that, and it says drive not found. did the whole grub was fine, typed root (hd0,4) and it came back with drive not found, ????? now vistini is installed, but cannot access ubuntu part of hdd

---

### Post by _khAttAm_ on 2009-08-01
> **medic0079 said:**
> so tried that, and it says drive not found. did the whole grub was fine, typed root (hd0,4) and it came back with drive not found, ????? now vistini is installed, but cannot access ubuntu part of hdd

well.. maybe hd0 is not the drive or 4 is not the partition where your ubuntu is installed. Press tab after "root (hd" and if it shows nothing, press tab twice.. that should list the available harddisks.. do the same for the partitions.. that would be tab after "root (hdX,"..

hope this helps.

---

### Post by Idefix82 on 2009-08-01
The thread Greyfox linked to explains, what numbers to put in instead of hd0,4.

---

### Post by medic0079 on 2009-08-01
Thanks I figured it out, I had to enter grub from a su status I.E. sudo grub then it worked flawlessly, one question though grub still says windows xp on boot screen, not that this really matters, but is there an easy way to change this? if no no big deal...

---

### Post by Post Monkeh on 2009-08-01
> **medic0079 said:**
> Thanks I figured it out, I had to enter grub from a su status I.E. sudo grub then it worked flawlessly, one question though grub still says windows xp on boot screen, not that this really matters, but is there an easy way to change this? if no no big deal...

alt & f2
then put in
gksu gedit /boot/grub/menu.lst


 scroll down to the windows xp entry and change the title to whatever you want.  be sure to take a backup of the original first in case you stuff it up.

---

### Post by medic0079 on 2009-08-02
Sweet works perfectly.... now my vista partition is named
SH**ty Operating System
Thanks for all the help guys!!!

---

