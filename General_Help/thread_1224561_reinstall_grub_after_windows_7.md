---
title: "reinstall grub after windows 7"
date: 2009-07-27
forum: General Help
---

### Post by Crypty on 2009-07-27
Hey peeps. Here's my problem. I had ubuntu, with the OS in it's own 10gb partition, then 60 or so for my home dir, then I had another 20gb of unpartioned space. I wanted to try windows 7 so I installed it in my free space, and of course it wiped out my grub(been there, done that)

I am using a 7.04 desktop live CD to get to terminal but running into problems reinstalling grub.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        8754    60548985    5  Extended
/dev/sda3   *        8755        8767      102400    7  HPFS/NTFS
/dev/sda4            8767       12162    27265024    7  HPFS/NTFS
/dev/sda5            1217        1459     1951866   82  Linux swap / Solaris
/dev/sda6            1460        8754    58597056   83  Linux

```

My ubuntu boot partition is sda1.


```
grub> find /boot/grub/stage1

Error 15: File not found

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type

```

If I browse into my ubuntu OS partition in nautilus I CAN find /boot/grub/stage1
Any help is appreciated. Thanks.

---

### Post by merlinus on 2009-07-27
You might try this:

```
sudo grub
root (hd0,5)
setup (hd0)
quit
```

---

### Post by Crypty on 2009-07-27
This comes back: 
```
grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type


```

---

### Post by merlinus on 2009-07-27
From this, am I correct in that you have a separate /boot partition?

If so, win7 may have done some nasty things to it.

You might try:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Otherwise, try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by BoardStupid on 2009-07-27
I have just spent the weekend trying to troubleshoot the same problem. I even wiped my HDD, installed win7 first then put Ubuntu 9.04 on afterwards. I could not get any combination to work. At first I could only boot Windows, then only Ubuntu, then nothing at all. In the end I just gave up, reinstalled Ubuntu and put Win7 on a virtual machine. It's not the ideal solution and I was a bit upset becasue Win7 looks like a really good OS but if it won't play nice with others then it's no dice for me. 

Sorry I can't help you any.

---

### Post by Crypty on 2009-07-28
bizzump

---

### Post by 1/0 on 2009-08-04
Any solution?

---

### Post by martinbaselier on 2009-08-04
Try:
**sudo grub-install /dev/sda**
from the livecd. I've had the same problem in the past. Grub needs to know all partitions on the disk for it to work correctly. It could be that you need to replace sda with sda1. There will be an error if you pick the wrong one.

---

### Post by 1/0 on 2009-08-04
> **martinbaselier said:**
> Try:
**sudo grub-install /dev/sda**
from the livecd. I've had the same problem in the past. Grub needs to know all partitions on the disk for it to work correctly. It could be that you need to replace sda with sda1. There will be an error if you pick the wrong one.

Not to steal the thread but in [my case](http://ubuntuforums.org/showthread.php?p=7730398) that didn't work...

---

### Post by martinbaselier on 2009-08-04
no errors? Did you try both?

---

### Post by 1/0 on 2009-08-05
> **martinbaselier said:**
> no errors? Did you try both?

Yes, without errors... The only thing I get is a Windows error with XP (that I ended up with now after windows 7) complaining on some boot ini file but it's still booting fine...

---

### Post by 1/0 on 2009-08-05
Seems unplugging the PATA drive with windows resolves my problem with grub... I just don't understand why? BIOS?

---

