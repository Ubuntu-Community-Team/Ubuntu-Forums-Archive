---
title: "SSD -- /dev/sda: Input/output error"
date: 2011-06-25
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-25
> Error benchmarking: helper exited with exit code 1: Error reading 27099136 bytes at 2509258752 from /dev/sda: Input/output errorthis issue is also preventing me from making a copy/backup of the partition with gparted
which i decided i should do since i had a scare when booting today

unable to mount / i said fix it
then it said /var was not ready
i waited it became ready

i am running 10.04.2 would upgrading the kernel to get trim support fix it?

```
sudo fsck -t ext4 /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
System: clean, 247383/983040 files, 1394162/3907803 blocks
```
Solution: drive is under warranty and it needs to be used this is not software problem

---

### Post by Abir Valg on 2011-06-25
You can make a back-up of your partition by simply copying all folders like
/bin
/home
/lib
etc. into a different place.

TRIM only helps improve throughput when your disk is 75%+ full. More recent kernels do have TRIM support.

---

### Post by pqwoerituytrueiwoq on 2011-06-25
if i create a partition on another drive and copy the files to that drive wont they lose there permission settings and become owned my the copier?

---

### Post by Abir Valg on 2011-06-25
Only the topmost like /bin /lib /home will be owned by the copier. I assume that you will copy them as root. Right now they are owned by root anyway.

---

### Post by pqwoerituytrueiwoq on 2011-06-25
/home and /var are on a standard hdd and the issue is on / so i don't need to worry about them or /tmp

would rsync preserve the permissions?
so if i copy these as root there will be no issue right
bin
dev
lib
opt
sbin
sys
boot
etc
initrd.img
lib32
media
proc
selinux
vmlinuz

cdrom  grub  initrd.img.old  lib64  mnt         root  srv      usr  vmlinuz.old

---

### Post by pqwoerituytrueiwoq on 2011-06-26
tryed to copy with nutilus it said i need ed 8TB and i am copying form a 16 gb ssd
rsync froze 
so ticked i am about to reinstall witch is a all day process with my slow as hell Internet

---

