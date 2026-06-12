---
title: "Can't mount / won't recognise blank CD-R"
date: 2010-11-11
forum: General Help
---

### Post by pariate369 on 2010-11-11
Hi

I've searched the forums and found several posts for similar problems but haven't yet found a solution to my problem.

I first realised something was wrong when I attempted to burn a CD using  Brasero.  Brasero said "please replace the disc with a supported CD or  DVD".  I tried using K3b, Gnome Baker, Gnome CD Master and encountered  the same problem every time - they didn't recognise the blank CD-R in  the drive.  

In Gnome Baker I opened Edit => Preferences => Devices and  discovered that only one of my CD drives is listed with a mount point.   The CD-R drive (the one I need to burn CDs) doesn't have a mount point.

I tried using fstab to alter this by entering a new line so that it now reads:

[FONT=Courier New]/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/FONT] 

Back in the terminal, I entered 

cat /proc/filesystems  
which returned

[FONT=Courier New]nodev    sysfs
nodev    rootfs
nodev    bdev
nodev    proc
nodev    cgroup
nodev    cpuset
nodev    tmpfs
nodev    devtmpfs
nodev    debugfs
nodev    securityfs
nodev    sockfs
nodev    pipefs
nodev    anon_inodefs
nodev    inotifyfs
nodev    devpts
    ext3
    ext2
    ext4
nodev    ramfs
nodev    hugetlbfs
nodev    ecryptfs
nodev    fuse
    fuseblk
nodev    fusectl
nodev    mqueue
nodev    binfmt_misc[/FONT]


Running 

wodim --devices  

returned

-------------------------------------------------------------------------
[FONT=Courier New] 0  dev='/dev/scd0'    rwrw-- : 'PHILIPS' 'DROM6216'
 1  dev='/dev/scd1'    rwrw-- : 'HL-DT-ST' 'DVDRRW GSA-4164B'[/FONT]
-------------------------------------------------------------------------


I don't know if this is relevant, but these drives were listed in Gnome Baker as s**r**1 and s**r**0 instead of s**cd**0 etc.

I'm running Ubuntu 10.10.  

Can anyone help me please.  I found the actions I describe above by Googling and visiting a few sites.  I'm still a Linux noob I'm afraid.  I'm really stuck and it's horribly frustrating - I just want to burn a couple of iso files to CD!

Thank you.

---

### Post by cucu007 on 2010-11-11
Looks to me like you needs firmware upgrade. try search in cdfreaks and see if you find anything for that particular device. Report back.

---

### Post by pariate369 on 2010-11-16
> **cucu007 said:**
> Looks to me like you needs firmware upgrade. try search in cdfreaks and see if you find anything for that particular device. Report back.


Thank you so much for your response.  I looked into it and read that updating firmware can cause problems unless I know EXACTLY what I'm doing and install precisely the right driver... so I chickened out and have bought an inexpensive external CD drive instead.  Yes, I'm a coward as well as a Linux ignoramus ;-)

Thank you again.  Will mark this as solved.

---

### Post by cucu007 on 2010-11-16
> **pariate369 said:**
> Thank you so much for your response.  I looked into it and read that updating firmware can cause problems unless I know EXACTLY what I'm doing and install precisely the right driver... so I chickened out and have bought an inexpensive external CD drive instead.  Yes, I'm a coward as well as a Linux ignoramus ;-)

Thank you again.  Will mark this as solved.


I think you are doing the right thing, you can find a cheap drive these days at newegg, probably under $20 bucks.

---

