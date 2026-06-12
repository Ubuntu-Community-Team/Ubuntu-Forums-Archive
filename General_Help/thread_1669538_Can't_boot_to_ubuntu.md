---
title: "Can't boot to ubuntu"
date: 2011-01-17
forum: General Help
---

### Post by chroniccommand on 2011-01-17
So I've been using Ubuntu that I installed with Wubi for quite some time now. I decided to try Arch so I created a 37G partition off my main Windows 7 partition. But now I can't boot into Ubuntu D:

Once it boots it gives me a bunch of errors such as init=bootarg and couldn't find /host/ubuntu/disks/root.disk

Then it drops me into a shell. Please help I have tons of important things on the Ubuntu drive.

Thanks in advance

-chronic

---

### Post by chroniccommand on 2011-01-17
Also, here is the message I get when I boot:
stdin: error 0
Failed to read bootsector (size=0)
Failed to mount /dev/loop0 : invalid argument
The device '/dev/loop0' doesnt seem to have a valid ntfs
Maybe the wrong device is used?
Mount : mounting /dev on /root/dev failed : no such file or directory
Mount : mounting /sys on /root/dev failed : no such file or directory
Mount : mounting /proc on /root/proc failed : no such file or directory
....
Target filesystem doesn't have /dbin/init
no init found - try passing init=bootarg

Then it brings me into BusyBox 1.13.2

---

### Post by bcbc on 2011-01-18
You probably changed the partition number that Ubuntu is on. Can you run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the results?

---

### Post by mick222 on 2011-01-18
double post

---

### Post by mick222 on 2011-01-18
You can't run Wubi Ubuntu from the grub installed by arch as it is on the mbr of the drive .See this [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) thread not sure how it works but it boots after the windows boot manager where you select Ubuntu I think the arch install overwrites this. You'll probably have to go for a full install of Ubuntu

---

### Post by bcbc on 2011-01-18
Wubi boots from the windows boot manager via grub4dos - if you can boot windows, you can boot wubi. You can also boot a wubi install directly from grub.

---

### Post by chroniccommand on 2011-01-18
> **bcbc said:**
> You probably changed the partition number that Ubuntu is on. Can you run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the results?
I can't boot to a linux partition so I can't run an sh file.

---

### Post by bcbc on 2011-01-18
so the arch linux install failed - or you haven't got around to it?

you need to figure out which partition wubi is on. since I don't have much to go on, I'll assume some things, and you can correct me if I am wrong:

You boot your computer
You see a menu with Windows and Ubuntu
You select Ubuntu and you see the grub menu

If that's true, hit 'e' on the first entry and report what XY is where it says:
linux /boot/vmlinuz-xxxxx root=/dev/sd**XY**

Hit ESC to go back, then 'c' to go to the grub command line.

Enter:
search -s -f -n /ubuntu/disks/root.disk
echo $root

Report back what you see - it will be something like (hd0,3)

---

### Post by chroniccommand on 2011-01-18
> **bcbc said:**
> so the arch linux install failed - or you haven't got around to it?

you need to figure out which partition wubi is on. since I don't have much to go on, I'll assume some things, and you can correct me if I am wrong:

You boot your computer
You see a menu with Windows and Ubuntu
You select Ubuntu and you see the grub menu

If that's true, hit 'e' on the first entry and report what XY is where it says:
linux /boot/vmlinuz-xxxxx root=/dev/sd**XY**

Hit ESC to go back, then 'c' to go to the grub command line.

Enter:
search -s -f -n /ubuntu/disks/root.disk
echo $root

Report back what you see - it will be something like (hd0,3)
I get this output:
```

insmod ntfs
set root = hd0, 2
set root loop0
some other crap

```The XY = a2
/dev/sda2 is the partition. So I booted up a live disk of ubuntu, and mounted /dev/sda2 on /media but there was only the folder /host/ubuntu/disks then root.disk in it.

The first time it booted into busybox I tried creating /host/ubuntu/disks/root.disk because it couldn't be found(figured this may fix the problem).

---

### Post by bcbc on 2011-01-18
OK it's hard to help you because you're not following my instructions... 

I'm going to therefore guess... when you see the grub menu, hit 'e' - look within the 'crap' and find where it says *root=/dev/sda2* and change it to *root=/dev/sda3*

Then hit CTRL+X to Boot.

If that works, when you boot ubuntu, go to a terminal (CTRL+ALT+t) and run "sudo update-grub".

If this doesn't solve it - you'll need to download and [burn an Ubuntu CD]("http://www.ubuntu.com/desktop/get-ubuntu/download") and follow the instructions to produce the bootinfoscript.

---

