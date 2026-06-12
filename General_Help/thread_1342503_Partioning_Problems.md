---
title: "Partioning Problems"
date: 2009-11-30
forum: General Help
---

### Post by ajhunte on 2009-11-30
I am having trouble with creating a new partition/resizing my current linux partition. I am trying to install Windows 7 (I know, blasphemy) because I got a free copy from my school and wanted to try it out. I go into gParted and I see the following (i left out amount used and amount remaining to save time):

Partition;           File System;    Mount Point;      Size                         ;Flags
/dev/sb1;            ext3; ;                                     9.35 GB;                   boot
/dev/sb2;            extended;                             456.41GiB;               
     /dev/sdb6;     ext3;                  /;                   433.75                   ;
    /dev/sdb7;      linux-swap;                            ;11.33;
    /dev/sdb5;      linux-swap;                            ;11.33

From what I understand, Linux-swap systems are some form of RAM substitution or something that I dont fully understand. They were not there before I updated to 9.10, or at least I dont remember seeing them. I am not able to resize the partition sdb6 which I assume is the one that hold all of my data (because it is the only one with a mount point /). I am pretty new to linux (about 6 months on and off), but i am pretty well versed with the terminal and other stuff. I really just need to create a 30 GiB partition to put windows on so that I can easily sync my ipod and play Civ without having to fight with the quirks in Wine. It would also be nice to understand what I need to do if I ever want to put Mint on my computer at some point later.

---

### Post by ed-koala on 2009-11-30
You can't change your Ubuntu partition while booted into Ubuntu.  The partition needs to be unmounted, meaning not in use, meaning you need to boot from a live CD to do the resizing.

Linux has FreeCiv, very similar game (hint, hint lol).

---

### Post by Sin@Sin-Sacrifice on 2009-11-30
Windows 7 isn't blasphemy... it's actually descent for Microsoft. I use it 2 or 3 times a month for gaming.

---

### Post by RJ12 on 2009-11-30
Yes what you need to do is go into the Live CD disk that you used to install Ubuntu with (or any with gparted) and you then can resize any partition you want to (linux-swap only needs one so you should be able to delete one but can someone comfirm this, I believe Ubuntu detects your swaps and uses them.) If you install Windows 7 you will need to re-install GRUB (someone can tell you how) and then you need to make a NTFS partition for Windows 7 to sit on. Another way is to get a virtual solution like VMware Player 3 (I have and works nicely) or VirtualBox. But if you resize partitions please be careful. And yes you resize the one mounted as "/". Im not really good at explaining this but someone will come and post it in a better way:p

---

### Post by ed-koala on 2009-11-30
Installing Windows AFTER Ubuntu isn't really the best idea, it's much less trouble to do it the other way around as Windows doesn't play nice with others, like Ubuntu does.  Windows wants to be the only OS and won't "see" Ubuntu when you install it.

---

### Post by u.b.u.n.t.u on 2009-11-30
I was hoping this would show more useful information, but it doesn't. Nevertheless it is of casual interest. This is gparted showing an 80 HDD with Windows 7 "hosting" Ubuntu 9.10 installeation via wubi on a 15 (or was it 20) GB dedicated partition.

[IMG]http://img22.imageshack.us/img22/1365/screenshotdevsdagpartedt.png[/IMG]

From an installation of Windows, for example, Windows 7, installing Ubuntu 9.10 via wubi is very easy.

---

