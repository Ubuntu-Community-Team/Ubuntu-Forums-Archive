---
title: "disk check on reboot"
date: 2010-09-28
forum: General Help
---

### Post by DouglasAdams on 2010-09-28
since i installed 10.04 virtually every other reboot a disk check is performed. previously disk checks were pretty rare.
obviously i don't want to cancel these disk checks but i do have
2 questions:

1)
how does it decide when to do a disk check when rebooting?

2)
is there any way to pre-empt a disk check?
i.e.
run it when the machine is idle / quite so that it is less likely to occur during a reboot (thereby making for faster reboots).

---

### Post by VCoolio on 2010-09-28
First, compare your nick to my avatar :). Second, I have these commands for you, see if you can do something with it. Fsck is determined by a file.

sudo shutdown -F -r now >> force reboot + fsck 
sudo touch /fastboot >> (re)boot without fsck next time 
sudo touch /forcefsck >> (re)boot with fsck next time

---

### Post by DouglasAdams on 2010-10-03
cheers for that vcoolio.
is there any way to do the disk check while the machine is actually running please? i.e. as per scandisk in windoze (excepting system & pagefile disks).

---

