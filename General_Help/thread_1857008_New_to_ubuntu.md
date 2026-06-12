---
title: "New to ubuntu"
date: 2011-10-09
forum: General Help
---

### Post by thepallasbull on 2011-10-09
Hi All, I am new to ubuntu and i had 10.10 installed when i decided to install 11.04.Every thing went well and it worked fine for a few days then last night I get a kernel panic and 2 flashing lights on my laptop .They look like the cap locks and drive  Leds.My problem is this I dont know how to work around this and how can i recover my data without loosing it to a new install. I have ubuntu on a flash drive and can boot from it and my home folder with my user name saya i dont have permissions to access it .Any help would be greatley appreciated.Kind regards thepallasbull:(:(

---

### Post by jonkiribati on 2011-10-09
you can boot on a Live CD or Flash Driver and use the terminal with sudo to get administrator rights

---

### Post by coldraven on 2011-10-10
The most important thing is to make a backup of your data.
External USB drives are cheap these days and have plenty of space.
If 10.10 worked well for you then get a Live CD and boot up with that.
Then copy your home folder onto the external drive.
If you have files over 4GB (like movies) you need to first check the formatting of your USB drive.
You can do this by running gparted from the Live CD
If it is FAT32 I would re-format it to NTFS.

Once you have a backup you have the choice to fix what you have or re-install 10.10.
Remember that 11.04 is a bit experimental, you might want to wait a week and get 11.10 instead. I think it should have some improvements over 11.04.

---

