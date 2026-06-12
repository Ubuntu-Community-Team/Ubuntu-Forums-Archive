---
title: "scond OS on second HDD??"
date: 2011-09-05
forum: General Help
---

### Post by Antarctica32 on 2011-09-05
I have 2 HDDs. On one of them is just 10.04. And the other one is blank. I want to install natty on my blank one and be able to choose which one to boot into at startup. Is this even possible? All help of any kind is greatly apreciated, thanks in advance.

---

### Post by andrewthomas on 2011-09-05
Yes, just make sure to pick the right disk to install to during the installation.

---

### Post by Antarctica32 on 2011-09-05
So say I make a natty usb flash drive, boot from it and choose to install on my blank drive? making a flash drive now.

---

### Post by Antarctica32 on 2011-09-05
OK, so I booted into it and now it has prompte me to either install ubuntu 11.04 alongside 10.04, uprade 10.04 to 11.04, erase 10.04 and install 11.04, or something else.

---

### Post by IWantFroyo on 2011-09-05
Choose something else.
The installer uses GParted (as far as I can tell), so you should be able to click on the top right and choose the HDD.

This is just from me using GParted in everyday life. It might be different in Ubiquity. I'm not really sure.

---

### Post by Antarctica32 on 2011-09-05
Ok it gives me a list of places. It gives me /dev/sda and under that /dev/sda1 which is ext4 (this must be my 10.04) and also under /dev/sda is /dev/sda5 wich is swap. It also gives me /dev/sdb which has nothing under it. and when i click /dev/sdb it gives me only 2 options new partition table and revert. add, change, and delete or unclickable. And at the very bottom of the screen i have to selec the device for boot loader installation, and it gives me the options of /dev/sda, /dev/sda1, and /dev/sdb. Should I just select /dev/sdb for the boot loader, and not do anything for the stuff above?

---

### Post by Antarctica32 on 2011-09-05
what if i just take out my lucid hdd, install natty on the blank one, and then put the lucid one back? or do i need both to be in to be able to select one at boot?

---

### Post by Antarctica32 on 2011-09-06
bump

---

### Post by oldfred on 2011-09-06
You want to use manual install, so you can choose to install the grub2 boot loader to sdb. All the auto install options default grub's boot loader to sda.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by Antarctica32 on 2011-09-08
Ok thanks for the help. Once I get time I will try to do it. The thing is I didn't want to install it on my first hdd because it will take away room from my lucid install which I need And I didn't feel like cloning or backing up and my first hdd is pretty old and I don't know how much longer it has. And it's  about 40 gb

---

