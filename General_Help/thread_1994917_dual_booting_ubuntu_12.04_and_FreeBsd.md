---
title: "dual booting ubuntu 12.04 and FreeBsd"
date: 2012-06-03
forum: General Help
---

### Post by the great sayaman on 2012-06-03
i installed ubuntu 12.04 first and Free Bsd just today however i am having a few problems dual booting them through grub 2

i am following the instructions from this

[http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html](http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html)

however it then says to enter the following commands in the ubuntu live cd (which i have adjusted according to my computor)

```

$sudo mount /dev/sda1 /mnt
$sudo grub-install --root-directory=/mnt /dev/sda
$cat /boot/grub/device.map

```

this gives a installation of grub is done without a problem however when the cat /boot... comand is given then i get the following result

```
cat: /boot/grub/device.map: No such file or directory

```

---

### Post by oldfred on 2012-06-03
One of the recent updates to grub2 did away with device.map. It will use it if found from an old upgrade but just finds devices each time it needs them.

You should just be able to look at your partitions with fdisk and  see what is what. FreeBsd needs a primary partition?

Post this from Ubuntu's command line:

sudo fdisk -lu

I do not use FreeBSD, but someone posted this as their 40_custom entry:

[http://forums.freebsd.org/showthread.php?t=5918](http://forums.freebsd.org/showthread.php?t=5918)
menuentry "freebsd 8.0" {
    set root=(hd0,2,a)
    chainloader +1
}

---

