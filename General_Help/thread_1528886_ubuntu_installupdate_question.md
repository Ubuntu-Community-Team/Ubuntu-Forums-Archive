---
title: "ubuntu install/update question"
date: 2010-07-11
forum: General Help
---

### Post by ken poy on 2010-07-11
Hello i installed Ubuntu rel 9.10 download as a first time user.  all was fine until the update manager bugged me enough to update.  i allowed it to download and install the updates for rel 10.04. after the update i started having intermittent GRUB errors at boot.  i worked on this problem and without warning Ubuntu returned to rel 9.10.  the Linux kernel is still at level 2.6.31-21.    now my question.....
rather than do another update manager update i am considering a download of rel 10.04 and install from that.
i would then have a backup for rel 10.04.
my concerns are my user data i do not have a user partition.  also how would the install partition my hard drive.  i allowed the install to partition my 9.10 system.

my current FDISK output

not sure why devices show sda i thought they woud be hda    hard drive??
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        5527    44307270    7  HPFS/NTFS
/dev/sda3            9338        9729     3148740   db  CP/M / CTOS / ...
/dev/sda4            5528        9337    30603825    5  Extended
/dev/sda5            5528        9174    29294496   83  Linux
/dev/sda6            9175        9337     1309266   82  Linux swap / Solaris

if i reinstall i would add a user partition.

any comments or advice would be appreciated.    thanks    ken

---

### Post by mörgæs on 2010-07-11
A clean install is a good idea. 

You will need a backup of your /home directory and various settings, if you have changed xorg.conf, for example. 

During the install of 10.04, you will be asked how you want the drive partitioned, and then you can make a separate partition for /home.

---

