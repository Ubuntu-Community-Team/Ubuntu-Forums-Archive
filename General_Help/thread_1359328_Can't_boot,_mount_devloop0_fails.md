---
title: "Can't boot, mount /dev/loop0 fails"
date: 2009-12-19
forum: General Help
---

### Post by DLGirl08 on 2009-12-19
I'm fairly new to Ubuntu, started using it on my own system in July. I'm running Ubuntu 9.04 Jaunty
Jackalope on a custom-built system, specs are at the bottom of this post. I'm about ready to tear
my hair out over this one...

About a month ago, I had a drive partition failure on two of my HDD's, my primary storage drive and
my Ubuntu drive. Couldn't figure out exactly what caused it, but Windows said the partition was
deleted. I managed to make a back-up of the files using Windows XP and Active@ File Recovery, but
couldn't save the partition table itself. So, I re-partitioned the drive and restored the files.

I tried to boot Ubuntu, only to find that the device UUID had changed (naturally) and therefore
the linux kernel didn't know where to look for the root.disk file. I managed to decipher what
UUID had been assigned to the drive, but there are now two problems:

1. I don't know how to PERMANENTLY fix the command line, only change it for each individual boot in
the grub menu; and

2. When I give it the proper device UUID, it returns the following upon attempting to boot:

```
Mount: mounting /dev/loop0 on /root failed: Invalid Argument
Mount: mounting /dev/ on /root/dev/ failed: No such file or directory
Mount: mounting /sys/ on /root/sys/ failed: No such file or directory
Mount: mounting /proc/ on /root/proc/ failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg
```

then it dumps me out to initramfs

```
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Type "help" for a list of built-in commands

(initramfs):
```

which for some reason, when I use mount for ANYTHING, it returns:

```
mount: can't read /etc/fstab: No such file or directory
```

And, to make matters worse, for some silly reason my system will not boot from a CD with the Ubuntu
ISO (that I got from the [Ubuntu Main Site]("http://www.ubuntu.com/GetUbuntu/download")); it SAYS it's bootable, but my system always ignores it,
even when I set my BIOS to boot from CD. So, I am unable to use the Live-CD recovery
features. I also have no internet connection at home, so I can't do updates at this point in time. I
suppose I could lug it to my friend's house 2 towns over, but I'd rather not if it can be avoided.

Please, somebody help me get Ubuntu back! I know it can't be that I'm pointing it to the wrong directory,
the relative working directory is "/ubuntu/disks", and loop is set to "/ubuntu/disks/root.disk", the same
path I get when I look for it under Windows.

*PLEASE HELP ME!!!*

_SPECS:_
AMD 2600+
ASUS A7 v600 mobo
768 MB RAM
nVidia GeForce MX 440 64MB AGP GFX card
4 Hard Drives (12Gb, 20Gb, and 2x 40Gb)

I can't remember the kernel version, but it's vmlinuz 2.something (I think)... I'll be
back Monday (hopefully) with that info.

---

### Post by Sin@Sin-Sacrifice on 2009-12-19
Hrm... wow. You have any way to make a bootable usb drive and run fsck?

---

### Post by DLGirl08 on 2009-12-19
Whenever I attempt to boot from USB, my system BIOS hangs at "Verifying DMI pool data"...

Can't get KNOPPIX, QEMU, WinXP Micro, or DSL to run on it...

---

### Post by Sin@Sin-Sacrifice on 2009-12-19
[http://www.duxcw.com/faq/computer/dmi.html](http://www.duxcw.com/faq/computer/dmi.html) for the DMI hang... I think that might be causing the other problem.

---

### Post by DLGirl08 on 2009-12-21
I used LinuxLive 2.2 and managed to get a working Live USB Boot Drive...
So I'm in Ubuntu, running in Persistent Mode, and I try to run fsck on my root.disk...

```
ubuntu@ubuntu:/$ sudo fsck /media/Ubuntu9/ubuntu/disks/root.disk
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/media/Ubuntu9/ubuntu/disks/root.disk: recovering journal
fsck.ext2: unable to set superblock flags on /media/Ubuntu9/ubuntu/disks/root.disk
```

What the...?

It seems from what I've found browsing around that the file system is indeed corrupt,
and beyond recovery. If this is the case, and bad turns to worse, I can always wipe
everything and do a fresh install, but I like to consider myself at least *partially*
sane, and would prefer to recover as many files as I could before doing so.

Perhaps this issue should be moved to a new thread? Or maybe re-post this particular bit of info somewhere else?

---

### Post by DLGirl08 on 2009-12-22
Well, I finally caved in and re-formatted. Most of the files I had were available online anyway, I just didn't want to have to re-download them, since I don't have a connection at home. So, basically, this thread is now kaput.

Thanks for your help, Sin@Sin-Sacrifice; at least you got me started looking in the right direction for solving the USB issue.

---

