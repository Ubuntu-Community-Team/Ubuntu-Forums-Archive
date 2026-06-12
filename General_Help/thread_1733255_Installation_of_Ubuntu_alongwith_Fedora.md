---
title: "Installation of Ubuntu alongwith Fedora"
date: 2011-04-19
forum: General Help
---

### Post by geekcalledsick on 2011-04-19
Hello,

I have 3 partitions in my laptop. In one partition I got Windows 7 and in another Fedora 14.
What I need to do to install ubuntu in third partition? So bootloader of fedora is not affected?

---

### Post by zvacet on 2011-04-19
Install grub on Ubuntu partition,but you will have to make changes in Fedora grub to add Ubuntu.

---

### Post by geekcalledsick on 2011-04-27
How do i do that?

---

### Post by mpranav007 on 2011-04-27
@geekcalledsick
Ubuntu's grub is better, it properly detects all other oses..All you need to do is install Ubuntu, which will also install grub to the /dev/sda and will automatically detect your windows and fedora partitions..

---

### Post by geekcalledsick on 2011-04-27
I hope it wont write over the boot loader of fedora 14 and win 7...

---

### Post by geekcalledsick on 2011-04-27
how do i find grub in Fedora 14? boot loader is the same as grub? I already have got fedora on my laptop.

---

### Post by kiyop on 2011-04-27
You cannot be too careful about install of boot loader on MBR, although Grub2 is great.

I suggest you to copy the current MBR and following 62 sectors into a file.

Boot with Ubuntu live CD without connecting extra media such as USB pendrive or USB-HDD.
Click "Try ubuntu"
"Application" -> "Accessory" -> "Terminal"
```
sudo dd if=/dev/sda bs=512 count=63 > mbrbackup
```"Places" -> "Home"
and right-click "mbrbackup" and select "Copy"

Select some partition relating to Windows 7 from "Places".
Right-click in the openned window (nautilus file manager) and select "Paste".

The file "mbrbackup" is copied into Windows 7 partition.

---

### Post by Silent Warrior on 2011-04-27
You're, uh, sure you don't want to append instructions to that on how to restore the MBR from that file? ;)

(Nope, I don't trust myself to do it - I've hardly ever used dd, and the times I've actually needed to are even fewer.)

---

### Post by kiyop on 2011-04-27
Silent Warrior, you know that the best way to restore MBR from the copied file depends on the situation, do not you? :popcorn:
For example, if installer changed the partition after MBR was copied, partition table of copied MBR should not be restored.
So I think I should not write how to restore.
I think the person who understand well can restore MBR at his own risk.
I usually copied(dumped) the current MBR to a file before I write some boot loader to MBR.
The person who do not know well should ask how to restore such as in this forum.

---

### Post by kiyop on 2011-04-27
> **geekcalledsick said:**
> how do i find grub in Fedora 14? boot loader is the same as grub? I already have got fedora on my laptop.
I do not know well about Fedora, but it may be "grub legacy(version 0.9...)" of "grub2(version 1.9...)".
Type in terminal the following, then the version of Grub your Fedora uses will be shown.
```
# grub-install -v
```("#" means you should get into root privilege. You need not type "#".)
My Fedora (with kernel 2.6.35.11-83.fc14.i686.PAE) uses Grub legacy (GNU GRUB 0.97=grub legacy) although I do not know it is default of Fedora(14).

And you can know version of grub or kind of boot loader installed on MBR by the following
```
# dd if=/dev/sda bs=2 count=1 2>/dev/null|hexdump -v -n  2 -e '/1 "%x"'
```"eb5e" -> Grub4dos ? fbinst ?
"eb48" -> Grub legacy
"eb4c" -> Grub 1.96 (Grub2)
"eb63" -> Grub 2

Or you can know by executing "boot info script".
You can get boot info script at [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

