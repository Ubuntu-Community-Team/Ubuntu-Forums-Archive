---
title: "No Bios or boot selections after windows hibernate"
date: 2010-04-12
forum: General Help
---

### Post by gjohny on 2010-04-12
. I had a dual boot umbutu 9.04 & xp Toshiba laptop satellite A15-S1292, (old bad battery).  I use it mostly in linux but had been working in Windows, it may have hibernated and the next boot may have been to Linux. Now it boots straight into Ubuntu login screen that looks like it is may be returning from hibernate (don't use it normally).  
On boot don't see the normal BIOS announcement or screen allowing the selection of boot device.  Doesn't boot Live CD from CD Rom or Suber Grub CD.  When I examined the Windows mount receive warning that it could not be mounted as it was hibernated. I followed the suggested mount -t -ntfs -3g -o remove_hyberfile /dev/sda1 and can now access the windows partition.  
Boots still return to the same linux login screen. Don't seem to be able to boot from anything else. 
The windows partition has the boot selected in Fdisk. 

I need to get back to dual boot and BIOS selections.

---

### Post by gjohny on 2010-04-12
Also selecting F1, F2, F12, & Del don't seem to help.

---

### Post by cr@ss on 2011-11-28
I believe this is relate to the issue resolved by this post [http://ubuntuforums.org/showthread.php?p=11497286#post11497286](http://ubuntuforums.org/showthread.php?p=11497286#post11497286)

In the linked post its windows instead of linux that is always booted to.

---

