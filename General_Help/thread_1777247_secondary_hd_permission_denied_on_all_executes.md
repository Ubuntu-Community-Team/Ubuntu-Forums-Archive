---
title: "secondary hd permission denied on all executes"
date: 2011-06-07
forum: General Help
---

### Post by coosadog on 2011-06-07
I completely switched to Ubuntu 6 months ago. I kept my secondary sata hd as ntfs for a while but started having permission problems. I switched it to ext4 and that worked for a while but then it started having permission problems again. Specifically, I can't execute anything on that hd drive. I converted it to ext2 and it still didn't help. I have 2 executable modules that I moved up to the root directory to make this simple and they look like this:


tom@tom-desktop:/media/sda1$ ls -l
total 3088
-rwxr-xr-x   1 tom  tom  3099451 2011-04-23 16:36 bochs
-rwxr-xr-x   1 tom  tom    26064 2010-09-11 08:48 bzip2

if I try to execute either here is what I get:


tom@tom-desktop:/media/sda1$ ./bzip2
bash: ./bzip2: Permission denied

or


tom@tom-desktop:/media/sda1$ sudo ./bochs
[sudo] password for tom: 
sudo: unable to execute ./bochs: Permission denied

Can someone point me in the correct direction here??

---

### Post by sisco311 on 2011-06-07
How do you mount the partition?

Please post the output of:
```
mount
```
```
cat /etc/fstab
```

---

### Post by coosadog on 2011-06-07
Thanks!  It's auto mounted by ubuntu. This fstab looks wrong:

UUID=a34dfc89-e629-46f5-af15-2863d42f6906 / ext4 defaults 0 0
UUID=e4234282-b254-4043-b868-5904decba4cc swap swap sw 0 0
UUID=54ab55f6-130e-47a7-ac03-e7daa2510e01 /media/sda1 ext2 group,user 0 0

shouldn't it be more like this?

/dev/sda1       /               ext2    errors=remount-ro 0       1
UUID=e4234282-b254-4043-b868-5904decba4cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by coosadog on 2011-06-07
I'll have to study the fstab I suppose. That first one, ext4, is my primary drive.  ext2 one is secondary. I don't know much about fstab but I guess maybe I'd better learn. I was hoping MountManager would do this for me...

---

### Post by sisco311 on 2011-06-07
The **user** mount option implies the  options  **noexec, nosuid**,  and  **nodev** (unless overridden by subsequent options, as in the option line **user,exec,dev,suid**). That's why you can't execute files on the partition.

Ubuntu defaults to **relatime** for ext3/ext4 and you should use the **defaults** option for ext2.

The  root filesystem  should be specified with a fs_passno  of 1, and other filesystems should have a fs_passno of 2. fs_passno is last filed in the fstab. It's used by[noparse] the fsck(8) program to determine the order in which filesystem[/noparse] checks are done at reboot  time.

Also you should add **errors=remount-ro** for the root partition.

So, I would suggest you to edit your fstab file to look like this:
```

UUID=a34dfc89-e629-46f5-af15-2863d42f6906 / ext4 **relatime,errors=remount-ro** 0 **1**
UUID=e4234282-b254-4043-b868-5904decba4cc swap swap sw 0 0
UUID=54ab55f6-130e-47a7-ac03-e7daa2510e01 /media/sda1 ext2 **defaults** 0 **2**
```

Of course, create a backup before you edit it:
```
sudo cp /etc/fstab /etc/fstab.backup
```

To edit the file, run:
```
gksu gedit /etc/fstab
```

For details, check out:
[thread=283131]How to fstab[/thread]
```
man fstab
```
and
```
man mount
```

---

### Post by coosadog on 2011-06-07
Ha! I beat you to it and luckily did what you suggested. It works now/again!  Thank you so much for helping me though.  Maybe I'll remember this for future reference but at my age, probably not...

---

### Post by sisco311 on 2011-06-07
I'm glad you figured it out.

Don't forget to mark this thread as [SOLVED] (see the link in my signatures). It will help others to find an expedient solution for their own issues.

---

