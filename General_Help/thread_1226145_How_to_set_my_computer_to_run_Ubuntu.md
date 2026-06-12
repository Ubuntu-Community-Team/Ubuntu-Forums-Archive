---
title: "How to set my computer to run Ubuntu"
date: 2009-07-29
forum: General Help
---

### Post by rigao on 2009-07-29
Hello everyone.

I have a laptop (dell inspiron 1545) where i dualboot Windows XP and Ubuntu.

I'm planing on getting rid of the WindowsXP partition and use wine (or a virtual box whenever wine wont work) to run windows programs (which I need) and I don't want to do anything before I get all well planned.

What I want?
-I want to have Ubuntu 64 bits as my primary OS, booting as fast as possible.

-I want to have 2 other partitions for other operating systems, just to play with them. Maybe one to have 1 super-fast OS just to surf the net, the other one, to install Windows 7 if I want to look at it, or, I don't know, whatever I decide. But, apart from Ubuntu, 2 other OS, one for sure linux, the other one may be windows or linux.

-I want another partition, very big, for data. It may or may not be accessible for windows (I mean, if your advice is to make it ext4, obviously windows wont access it, but if your advice is to make it NTFS just in case, because in this kind of scenario the data format is not important, then it will go to NTFS). As my laptop has 320Gb, I think I have plenty of room. What I actually do is 20Gb for each OS and the rest for the data partition.

-I want to have a virtual box for windows.

Ok, so this things are what I'm seeking for my computer. Now, can you answer me this questions so I can plan it ahead?

-Partition system: How would you partition my 320Bg hd? Which filesystem for each partition? Basically: Do I need a partition for \boot if I'm planing on more than 1 linux OS? Would you use a \home for every linux OS, or would you make sepparated ones? How do I order this partitions to optimize boot time? /boot, /, /home, other OS, data (whetever filesystem)

-How can I optimize Ubuntu 64 9.04 boot time (nowadays it boots in 51s in my inspiron, from grub to desktop display in a ext2 partition, which I think it is veeery slow)? Just link me to this, as I'm sure it will have been discused plenty of times, but I have been searching for tips into 9.04 but couldnt find any specific on this distro. Be aware that it is a laptop, nobody else will have access to it w/o my permission so I plan to login directly into my session.

-Which other OS would you recommend me? I'm not an advanced linux user, but I'm willing to learn some things, this is why I want to have this other OS ;) Nowadays I have archlinux installed, but I'm having problems with drivers, and its more an annoyance than anything else. It doesn't seem to boot super-fast either.

-Where do I put the data of the virtual box, which seems to need 10Gb of space? I don't want it in the big partition, as this partition is for data, not OS.

-How can I save my configuration so I can load it when I reinstall everything?

Ok, for now, this is all :-) I hope someone is kind enought to help me make a good laptop out of this.

---

### Post by rigao on 2009-07-30
If this has already been asked, or is not this forum where I need to post it, just tell me.

---

### Post by lisati on 2009-07-30
try looking the installation subforum rather than at the watercooler

---

### Post by coffeecat on 2009-07-30
**rigao**, I've posted a reply to the post you made in the thread in the Installation sub-forum.

---

### Post by meka4996 on 2009-10-25
[http://ubuntuforums.org/showthread.php?t=1300461](http://ubuntuforums.org/showthread.php?t=1300461)
Partition Table Design Scheme for Multi Boot Many/Multiple Linux Distro, Windows OS, or Mac, using Grub bootloader

---

