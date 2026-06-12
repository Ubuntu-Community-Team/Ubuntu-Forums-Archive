---
title: "Hard drive recovery, help!"
date: 2006-06-11
forum: General Help
---

### Post by pianoboy3333 on 2006-06-11
So, recently, I constructed an external hard drive, which I use to store my backup on. I also wanted to get some linux distros on there also (you can see the problem starting already). Let's start with the layout of my drives:

sda (my main internal sata hard drive) - 160 GB
sda1 - main ubuntu partition - about 47 GB - EXT3
sda2 - windows xp home partition - about 100 GB - EXT3
sda3 - linux swap partition - about... what ever's left... - SWAP

sdb (my external) - 80 GB
sdb1 - 40 GB - EXT3
sdb2 - 30 GB - EXT3
sdb3 - 5 or 7 GB (something like that) - FAT32, so all computers can access it
sdb4 - 2ish - SWAP

So, I have been trying to install fedora, and ubuntu, and xubuntu on the drive during the past month. I know xubuntu has worked in the past, and fedora hasn't when it's the main one on the drive, so I chose to go with xubuntu as my main distro on the drive. Now, my backup of my main system was stored on sdb2. I got into my xubuntu desktop cd (6.06) and started to install.

I got through all the menus fine, I then chose custom for partitioning the hard drive and such. I specifically chose sdb1, it said 40 gb, and then sdb4 for swap. Everything else was placed somewhere in /media.

The shock came when I rebooted and couldn't boot off of my USB sdb drive. No shock, I just thought some xorg.conf file or grub menu.lst file was unconfigured, so I booted onto my main sda drive. And there it came, of course freakin windows was untouched, but it seems xubuntu got installed to sda1 instead of sdb1, over my main partition, with all of my programs, and work. Not good.

My question is, I'm aware that until something over writes the physical part of the hard drive, the info can still be there.

Does anyone know of a way I can go about recovery, and place I can send the drive cheap, or any good programs I can use?

---

### Post by bohboh on 2006-06-11
I have used this before with varied success.

[http://www.ontrack.com/easyrecoverydatarecovery/]("http://www.ontrack.com/easyrecoverydatarecovery/")

---

### Post by pianoboy3333 on 2006-06-11
I'm just not sure if I am going to get anything to work because I somewhat wrote over it...

---

### Post by bohboh on 2006-06-11
[QUOTE=pianoboy3333]I'm just not sure if I am going to get anything to work because I somewhat wrote over it...[/QUOTE]

Ah, misread your post. That will be a problem. But i would definately give it a go.

It may be too late but read [this]("http://support.ontrack.com/cgi-bin/ontrack.cfg/php/enduser/std_adp.php?p_faqid=868&p_created=1042048336&p_sid=ap1WyP9i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PWRmbHQmcF9ncmlkc29ydD0mcF9yb3dfY250PTE0NCZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9MyZwX3BhZ2U9MQ**&p_li=&p_topview=1") regarding data recovery dos and donts.

---

### Post by pianoboy3333 on 2006-06-11
ok, thanks

---

### Post by pianoboy3333 on 2006-06-11
Damn I'm so screwed, anyone else got any ideas?

---

### Post by pianoboy3333 on 2006-06-13
No one has anyother ideas as to programs, or companies where I can send it?

---

### Post by TuxCrafter on 2006-07-13
[http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm)

maybe this will help you

---

### Post by TuxCrafter on 2006-07-13
I did some small searching and found these programs:

Foremost and TestDisk

---

### Post by TuxCrafter on 2006-07-13
The basic for recovery to work is when the files are not yet overwritten on the disk if you installed data over your data that you want to recovery it will be difficult

---

