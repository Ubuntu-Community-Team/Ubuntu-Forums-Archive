---
title: "Urgent Help do not have rights for partition"
date: 2011-01-19
forum: General Help
---

### Post by sunseeker888 on 2011-01-19
Hello


I have this big issue.


I have 4  hard disk, and one of the harddisk, where all my backups are stored, it says I do not have right to access

Please I really need to access my files.


using gksudo nautilus, I can go in the parition, but cannot copy or move the files.

I need help here, how to change that partition permission

---

### Post by sunseeker888 on 2011-01-19
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc  proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=80339bbe-1f1c-4e8a-8ca6-dbd2fa581442  /      ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=83764fba-8e5b-4f92-b675-f05d1bb5aeb1  none   swap  sw                   0  0  

UUID=d246df40-72c4-4c08-87f1-2a120a8a7691/data ext4  defaults             0 0

---

### Post by sunseeker888 on 2011-01-19
badboy@Supermax:~$ sudo mkdir /storage
badboy@Supermax:~$ ls -l/dev/disk/by-uuid
ls: invalid option -- '/'
Try `ls --help' for more information.
badboy@Supermax:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2011-01-19 06:12 80339bbe-1f1c-4e8a-8ca6-dbd2fa581442 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-01-19 06:12 83764fba-8e5b-4f92-b675-f05d1bb5aeb1 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-01-19 06:12 83bbb35a-bd71-4f65-8670-a33ad0993e5c -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-01-19 06:12 d246df40-72c4-4c08-87f1-2a120a8a7691 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2011-01-19 06:12 da5771ad-c1c1-42aa-8e1e-95e610cf65da -> ../../sdb1



I have the above then edited fstab and added

UUID=d246df40-72c4-4c08-87f1-2a120a8a7691/storage ext4  defaults             0 0

badboy@Supermax:/etc$ sudo mount -a
mount: mount point ext4 does not exist
badboy@Supermax:/etc$ 





it's saying point ext4 does not exist? can someone help is there a problem in fstab?

---

### Post by spook1980 on 2011-01-19
gksudo nautilus then once u got nautilus open right click on the file and go 2 the permissions tab u should b able to change permissions that way

---

### Post by sunseeker888 on 2011-01-19
> **spook1980 said:**
> gksudo nautilus then once u got nautilus open right click on the file and go 2 the permissions tab u should b able to change permissions that way



Hello

I have used gksudo nautilus, I can view the files, but canot do anything else.

It won't allowed me to change file access

---

### Post by sunseeker888 on 2011-01-19
> **spook1980 said:**
> gksudo nautilus then once u got nautilus open right click on the file and go 2 the permissions tab u should b able to change permissions that way




Thanks


I got it working . Thank you again

I did gksudo nautilus then click on SDD and changed permission of that drive

---

### Post by spook1980 on 2011-01-19
> **sunseeker888 said:**
> Thanks


I got it working . Thank you again

I did gksudo nautilus then click on SDD and changed permission of that drive

thats what the ubuntu comunity is there for. just glad i could be of some help

---

