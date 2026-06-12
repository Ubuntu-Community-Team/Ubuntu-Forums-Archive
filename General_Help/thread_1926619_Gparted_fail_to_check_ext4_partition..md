---
title: "Gparted fail to check ext4 partition."
date: 2012-02-16
forum: General Help
---

### Post by dancer_69 on 2012-02-16
Hello,
I've made an ext4 partition of all disk to store data, and after some problems with file copy(slow transfer), I tried to check the disk from gparted. 
The problme is that the checking stops immediately and on details I get the error:
ef2fsck -f -y -v /dev/sda1
e2fsck 1.41.14(22-Dec-2010)
/dev/sda1 has unsupported features FEATURE_R30 FEATURE_R31
e2fsck: Get a newer version

I have Ubuntu natty and there isn't a newer version on repositories, and also this partition created in this ubuntu installation and from gparted.

Any idea?

---

### Post by dancer_69 on 2012-02-17
Someone who can help?
I cannot even mount the disk after I've tried to check it from gparted. Now fstab, which I didn't touch it at all, give this error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I've checked the disk with hdd regenerator and hard disk sentinel before make this ext4 partition and I didn't get any errors.

---

