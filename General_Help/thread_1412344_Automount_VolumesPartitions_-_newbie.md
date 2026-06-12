---
title: "Automount Volumes/Partitions - newbie"
date: 2010-02-21
forum: General Help
---

### Post by Quarkrad on 2010-02-21
I have 9.10 and notice that when I look in Places none of my volumes/partitions are mounted - if I click on them I have to enter my user password to authenticate to gain access.   My problem is that (with some help) I have set up rsync so it runs when I shut down my PC and backs up my Home folder from a partition on sda to a partition on sdb - this is great but sometimes it works and sometimes it doesn't.
I have done some tests and discovered that if I use my PC and never manually mount my backup sdb partition the rsync does not work (I also have GAdmin-rysnc so I can run manually backup but this also will not run if I do no mount the sdb volume).  However, if I do mount the sdb backup partition and close down/restart then the backup works.  What I need is my sdb backup partition to be automatically mounted every time I switch on - can this be done?  I'm sure I had this working in 9.04 (auto mounting) but 9.10 seems not to like it.

---

### Post by mikewhatever on 2010-02-21
You'll need to add a line to fstab. Can you post the output of the following command from Terminal:

sudo fdisk -l

---

### Post by Quarkrad on 2010-02-21
Thanks for the reply and sorry for the long delay.  Here is the output:

[B]Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c26fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda2   *        3188        7011    30716280    7  HPFS/NTFS
/dev/sda3            7012       48641   334392975    f  W95 Ext'd (LBA)
/dev/sda5            7013       26772   158722200    7  HPFS/NTFS
/dev/sda6           26773       48513   174634551    7  HPFS/NTFS
/dev/sda7           48514       48641     1028128+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005a4cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2        1276    10241406    7  HPFS/NTFS
/dev/sdb6            1277       60801   478134531    7  HPFS/NTFS[/B]

My day to day Ubuntu system is sda1  and my backup partition is sdb6

---

### Post by mikewhatever on 2010-02-21
I typed all the follwoing and then remembered there was a gui way. Use whatever you like.

[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

----------------------------------------------------------------------------------------------

So, sda6 is the one you want automounted (fstab editing).

1. Create a mount point.

sudo mkdir /media/sda6

2. Backup the current fstab

sudo cp /etc/fstab /etc/fstab-original

3. Open fstab for editing

gksudo gedit /etc/fstab

4. Add the following to /etc/fstab

/dev/sda6 /media/sda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

save and exit.

---

### Post by Quarkrad on 2010-02-21
Mike - many thanks.

---

