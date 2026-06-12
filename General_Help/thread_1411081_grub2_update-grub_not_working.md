---
title: "grub2 update-grub not working"
date: 2010-02-19
forum: General Help
---

### Post by oshunluvr on 2010-02-19
I'm I the only one who is having this trouble???

set up:
four sata drives, all partitioned the same.

first installed: kubuntu karmic on /dev/sda5, with grub2 on mbr of sda

then installed kubuntu karmic on raid0 device with /boot on /dev/sdb2

then installed opensuse 11.2 on raid0 device with /boot on /dev/sdc2

no amount of "update-grub" detected the other installs. edited 40_custom to include new installs but they never showed up in the grub2 menu at reboot - even though they were in fact in grub.cfg at the time.

got tired of this and created stand-alone partition for grub2. installed and setup grub2 on it, ran grub-mkconfig and created new grub.cfg but same as before - no other installs detected and custom entries in grub.cfg but not at reboot.

driving me nuts at this point!

booted to second kubuntu install via chainload and grub2 there detected first kubuntu install but not opensuse. friken weird...

so best I can see at this point:

since my initial kubuntu install was not on a raid0, raid0 isn't loaded by grub2. I added "insmod raid" and "...mdraid" to my dedicated grub but nada. Seems odd because all the raid0 installs have dedicated /boot in non-raid, but thought I'd try it.

Also I am using reiserfs on every partition EXCEPT the initial kubuntu install and yes, I've added "insmod reiserfs" to grub2.

It seems there is something I've missed or borked so I am going to re-install grub2 to my dedicated partition from one of the raid0 installs and see if that helps.

I would appreciate any suggestions or witty remarks.

---

