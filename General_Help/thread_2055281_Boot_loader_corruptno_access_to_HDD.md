---
title: "Boot loader corrupt/no access to HDD"
date: 2012-09-09
forum: General Help
---

### Post by MattKimura on 2012-09-09
[INDENT] 							I got a big problem on my hand, I may lose everything on my harddrive if I don't fix it. It's life or death right now.

So this is what happened, I installed Linux from a usb flash drive, it  went well, when I restarted, the boot loader was there, and I booted up  Linux normally. But I get a problem where when I try to install an app  from software manager, it'll download half way, or almost half then  suddenly stop. I always get this prob (I've installed Linux like 3-4  times on this HDD so far)
I restarted my computer to get into windows 7, but the bootscreen is  corrupted, saying the partition doesn't exist, and Im able to typ ein  commands. Says Grub rescue on the left of the command lines.
I tried using the recovery partition to use startup repair to fix the boot, but it isn't working this time.
All I can do is boot Linux from my usb flash drive, and hope for help somewhere on a forum.

I remembered that I installed Linus before, so now I have two partitions  for Linux now. They both showed up in the boot loader. I might be able  to use Gparted on Linux to fix my partitions. For some reason, I can't  even load the C drive from linux when I usually can. It says mount when I  right click it. which does nothing.

Screenshot of gparted:
http (space<-- delete) ://img849.imageshack.us/img849/4503/screenshotfrom201209090.png

The two 58 GB partitions are my Linux partitions. The OS partition is my main one with windows 7 installed on it.


If anyone can help me with this problem, it'll be the nicest thing anyone can do! 						[/INDENT]

---

### Post by opensshd on 2012-09-09
Installing software is particularly disk intensive. How old is the disk?

Hate to jinx you, but if your hdd is starting to fail on prolonged use, sounds like you could have a hardware issue.

I would try booting from the usb liveOS, opening the hard disk and see if you can recreate the disk failure by copying some largish file.

Also, if you search disk utility from gnome's menu (you're running 12.04 Ubuntu/gnome?), there are some tests you can run to give an indication of disk health.

I would rule out the possibility of a failing disk before going on to fixing what's on it. :)

---

### Post by MattKimura on 2012-09-10
Problem solved!! I'm finally back on Windows 7, removed the Linux partition, restored my boot to normal.
My solution:
Using Linux from my usb flash drive, I ran a command in the terminal:

sudo apt-get install lilo sudo lilo -M /dev/sda mbr Then I restarted, and the boot menu was working again, but its  the Linux grub menu. When I loaded up windows 7, I would get a black  screen with my cursor on it. So I restarted, launched my recovery  partition and did a system restore from a few days ago. Now Im able to  get into windows 7 normally :)
I removed the Linux partitions, got  all my space back. If I do a Linux install, I'll either do Mint4win, or  what someone suggested, Knopper.

---

