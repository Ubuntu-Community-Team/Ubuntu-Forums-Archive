---
title: "Cant automount"
date: 2010-02-08
forum: General Help
---

### Post by rock4christ on 2010-02-08
I installed Storage Device Manager and can't automount my Windows 7 partition. It doesn't show up in Storage Device Manager. When I mount the partition, it comes up as /media/286CC2A6397A0F2A instead of sda# like normal drives.

---

### Post by DeMus on 2010-02-08
> **rock4christ said:**
> I installed Storage Device Manager and can't automount my Windows 7 partition. It doesn't show up in Storage Device Manager. When I mount the partition, it comes up as /media/286CC2A6397A0F2A instead of sda# like normal drives.

So you can mount it. When it shows up in /media it is mounted.
Okay, the name is different from what you expect but the drive is mounted.
Can you read it as well? Can you see what's on the drive and read files?

---

### Post by rock4christ on 2010-02-08
> **DeMus said:**
> So you can mount it. When it shows up in /media it is mounted.
Okay, the name is different from what you expect but the drive is mounted.
Can you read it as well? Can you see what's on the drive and read files?

yes. I can read from it as well. I need to be able to automount, and write to it though.

---

### Post by rnerwein on 2010-02-08
hi
1. open a terminal and "sudo /bin/bash"
2. mkdir /your_mountpoints
3. edit your fstab - here are my entries in fstab - and it works for me ( installed 9.10 karmic koala out of the box and it's doing the job for me)

 /dev/sda2 /vista_root ntfs defaults,umask=000        0    0
 /dev/sda3 /vista_data ntfs defaults,umask=000        0    0

--> sda2 and sda4 have to change to your behavior !
--> see man mount for information about "defaults"

4. try: mount -a (you will see if your changes works)
5. exit your root shell

ciao

---

### Post by rock4christ on 2010-02-08
I tried editing my fstab manually, from

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda3 during installation
UUID=0ef57e9b-113f-49f5-9790-2c8a96934eff  /              ext4         errors=remount-ro        0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0 
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000  0  0  
/swapfile1 swap swap defaults 0 0

to > # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda3 during installation
UUID=0ef57e9b-113f-49f5-9790-2c8a96934eff  /              ext4         errors=remount-ro        0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0 
/dev/sda1                                  /media/Sda1    ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000  0  0  
/swapfile1 swap swap defaults 0 0

and I get
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/sda1

---

### Post by superstalker on 2010-02-08
install pysdm

When installed, press "Alt + F2"

 	Code:
 	 sudo pysdm 
Follow instructions and the hard drives will be mounted everytime  you log in.

---

### Post by rnerwein on 2010-02-08
> **rock4christ said:**
> I tried editing my fstab manually, from



to 

and I get
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/sda1

hi
Error 1 means EPERM  - operation not permitted
you forgot to be super user (root)
try: sudo mount -a
 
ciao

---

### Post by rock4christ on 2010-02-08
> **superstalker said:**
> install pysdm

When installed, press "Alt + F2"

 	Code:
 	 sudo pysdm 
Follow instructions and the hard drives will be mounted everytime  you log in.

I have it. problem is my windows partition(sda1) doesnt show up in it. only sda2(my ntfs data partition) and sda3(my ext4 ubuntu partition) do

---

### Post by superstalker on 2010-02-09
Does the partition show up in Disk Utility? If so, check the health.

---

### Post by rock4christ on 2010-02-11
> **superstalker said:**
> Does the partition show up in Disk Utility? If so, check the health.

how would I do that? also, it is the same physical disk as the other ones that show up.

---

### Post by rock4christ on 2010-02-12
found a simple solution. I just added an entry into fstab

---

