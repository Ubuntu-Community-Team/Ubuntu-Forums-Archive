---
title: "Unable to Hibernate/Resume but Suspend/Resume works fine"
date: 2010-12-20
forum: General Help
---

### Post by harbhag on 2010-12-20
Hi,
My laptop (Dell Inspiron N5010) is unable to hibernate, when I click on hibernate it just goes blank and them come back to login screen however suspend works fine. Below is the information that might help you to solve my problem

```
uname -a
Linux harbhag 2.6.37-10-generic #24-Ubuntu SMP Thu Dec 16 17:54:02 UTC 2010 x86_64 GNU/Linux

lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu natty (development branch)
Release:	11.04
Codename:	natty

sudo blkid

/dev/sda1: UUID="1760a22e-f8db-4909-9c6d-938d022032ae" TYPE="ext4" 
/dev/sda2: UUID="989b20ee-4416-49dc-9c90-5c804785ab89" TYPE="swap" 
/dev/sda3: LABEL="data" UUID="7ab1b1c8-9381-4f42-ad02-5b4b9de8de26" TYPE="ext4"

sudo fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6810    54701293+  83  Linux
/dev/sda2            6811        7890     8674304   82  Linux swap / Solaris
/dev/sda3            7891       60801   425007607+  83  Linux


/etc/initramfs-tools/conf.d/resume

RESUME=UUID=989b20ee-4416-49dc-9c90-5c804785ab89

/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1760a22e-f8db-4909-9c6d-938d022032ae /               ext4    errors=remount-ro 0       1
UUID=989b20ee-4416-49dc-9c90-5c804785ab89       none            swap    sw              0       0

free -m
total       used       free     shared    buffers     cached
Mem:          3827       1303       2523          0        113        449
-/+ buffers/cache:        740       3087
Swap:         8470          0       8470



```

I have 4GB ram and total 8GB swap space. My laptop uses ATI Radeon Mobility HD 5000 series and it uses proprietary drivers installed via jockey.

---

