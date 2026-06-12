---
title: "Dual boot, Ubuntu and XP"
date: 2011-10-12
forum: General Help
---

### Post by Jo.Buntu on 2011-10-12
dual booting Xp and ubuntu. I just installed 11.04 to a new partition with XP still being in a partition. However, after the installation it gives me no option to boot into ubuntu. It is still using the normal loader and not GRUB2 for some reason. Do I need to edit my mbr? what should I do to get this dual boot going?

---

### Post by Dangertux on 2011-10-12
This should help you recover your boot loader

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Jo.Buntu on 2011-10-12
no.... I installed Ubuntu, not windows. The computer had windows by default and I just installed ubuntu alongside it. I need to know how to make it so I can boot ubuntu.

However I will try that first solution anyways. gahhhh so tired.

---

### Post by Dangertux on 2011-10-12
If you're really tired you should get some sleep. However -- if you have the Windows bootloader that link WILL help you, since you will need to install GRUB to be able to boot into Ubuntu.

Give that link a chance, you will get the result you want.

---

### Post by Jo.Buntu on 2011-10-12
Worked. Time to sleep meow.

---

### Post by mastablasta on 2011-10-12
did you use Wubi to install?
it would be best to post results from running bootinfoscript,before people can give any advice. They might give oyu the wrong one. 
 
Boot the system using LiveCD/liveUSB, download the script and follow the instructions found here:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
this script should show us what is happening during boot and where grub is installed. it might also indicate the problem.

---

### Post by mörgæs on 2011-10-12
Changed the thread title to a more descriptive one.

If 'worked' means that the problem is solved, then please mark the thread so.

---

