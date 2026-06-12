---
title: "First time ubuntu user"
date: 2011-03-10
forum: General Help
---

### Post by abu46 on 2011-03-10
hello guys:D

this is my first post on the forum:P

i wana start using ubuntu for the first time in my life and want some help regarding installation:confused:

-i will be installing it along with windows 7 ultimate 64bit edition

-is the "ubuntu-10.10-desktop-amd64.iso" right for me??

-i want to install it via usb so i downloaded Universal-USB-Installer-1.8.3.4

-by reading various guides on installation i am confused about what partion to install ubuntu in
i have 2 partitions on my primary hdd, C:\ with windows and the D:\ for downloads
i want to install ubuntu in D:\, so will ubuntu wipe out\format the D:\ drive.
is this right way or should i install it on C:\, i dont want to resize or create new partitions

-can installing ubuntu corrupt the boot loader of windows and what other precatons should be taken??

awaiting your replies..................

---

### Post by xbonez182 on 2011-03-10
Hey, I'm also a first time user. I installed 10.10 onto my C: drive alongside XP. This hasn't proved problematic to me so far (only 4 days ago) and has wiped no data. All it does is throw up a boot menu each time you startup asking you either WinXP or Ubuntu. 
 
Having seen how it works, next time I will install it onto another partition or try to format and make it a sole install as I'm quite happy with my first impressions (my only issue being screen res)
 
And yes the *.iso image you have is the right one. If you are installing it from USB, extract it first I think. I did it from CD. 
 
Hope this helps.

---

### Post by mrtn474 on 2011-03-10
Hi :) 

Yeah, I'm also a first time user and I've been using it for only a week I think and this forum has been very helpful. 

I wanted to create a new partition on my drive but unfortunately it would have been problematic I believe. So what I did is i used [wubi]("https://wiki.ubuntu.com/WubiGuide") to install it within windows just as any other program. According to the ubuntu website, it is the safest way.

---

### Post by indytim on 2011-03-10
Rather than re-inventing the wheel, I'd suggest that your first stop should be the sticky at the top of the Absolute Beginner's Forum (New to Ubuntu)
[http://ubuntuforums.org/showthread.php?t=801404]("http://ubuntuforums.org/showthread.php?t=801404")

Minor point.... there are also Ubuntu "Gals"

IndyTim / DataMan

---

### Post by abu46 on 2011-03-11
thnx for the rplies guys:D

@mrtn474
i guess wubi is the safest way to go, will try and report):P

---

### Post by rvchari on 2011-03-11
> **abu46 said:**
> hello guys:D

this is my first post on the forum:P

i wana start using ubuntu for the first time in my life and want some help regarding installation:confused:

-i will be installing it along with windows 7 ultimate 64bit edition

-is the "ubuntu-10.10-desktop-amd64.iso" right for me??

-i want to install it via usb so i downloaded Universal-USB-Installer-1.8.3.4

-by reading various guides on installation i am confused about what partion to install ubuntu in
i have 2 partitions on my primary hdd, C:\ with windows and the D:\ for downloads
i want to install ubuntu in D:\, so will ubuntu wipe out\format the D:\ drive.
is this right way or should i install it on C:\, i dont want to resize or create new partitions

-can installing ubuntu corrupt the boot loader of windows and what other precatons should be taken??

awaiting your replies..................

the ideal way to install will be like this
1)c: let ur windows be there undisturbed
2)d: delete the partition and reconfigure your partition table.
3) create partition table like this
=>mount point / = allocate say 25 gb min
=>mount point swap = min = twice the size of RAM you have (4 gb should be ideal)
=>mount point /home = max allowable (min 25 gb)
=>mount poing /Backup = remaining disk space to back up your data every now and then

install grub in master boot record (MBR)

you will feel using the dual boot very comfortable.

hope this suggestion will get you to where you need to.

download gparted live cd to create/edit partitions. this cd will become handy in the long run

---

### Post by abu46 on 2011-03-11
^^^^

thnx for the advice bro

there is a problem with deleting the d: partition as it has large amount of data on it and i cannot backup it up for some time

can ubuntu install on d: without deleting the data on that partition??

does the "wubi" method of create problem

---

### Post by Karlchen on 2011-03-11
Hello, abu46.

The Wubi installation is very unlikely to cause any trouble. The opposite is true. Wubi will allow you to preserve your C: and D: drives unmodified. Wubi will install Ubuntu on the drive which you specify and create a container file there which will be used as the Ubuntu *disk*. It will add an entry to your Windows boot menu which will allow you to boot (1) Windows (default) or (2) Ubuntu.

As a matter of fact I am writing this from my Wubi installation of Lucid Lynx right now. As this is an office machine, using Wubi was the only allowed way of installing Ubuntu on this machine. It has been running fine and without any hassle from the start and for the past 9 months now.

Guess, this instruction by psychocat may interest you: [Installing a dual-boot with Windows without partitioning]("http://www.psychocats.net/ubuntu/wubi"). - psychocat created a number of very helpful instructions. 

Kind regards,
Karl

---

### Post by abu46 on 2011-03-12
@Karlchen

thnx man :):)

---

### Post by rvchari on 2011-03-12
> **abu46 said:**
> ^^^^

thnx for the advice bro

there is a problem with deleting the d: partition as it has large amount of data on it and i cannot backup it up for some time

can ubuntu install on d: without deleting the data on that partition??

does the "wubi" method of create problem

wubi will not create any problem. but you might face problem for screen resolution or graphical interface (check out the threads related to this)

---

