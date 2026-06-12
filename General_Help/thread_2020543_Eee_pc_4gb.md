---
title: "Eee pc 4gb"
date: 2012-07-08
forum: General Help
---

### Post by BigMeme on 2012-07-08
Hi.I have a EEE PC 4 GB,and I want to install Ubuntu(now I have a Bodhi Linux wich is broken).in the past when I try it to install Ubuntu I received some error for low memory,the minimum is 4.4 or something like that.Now I want to buy a SD card (MICRO-SD 32GB KINGSTON)and on installation of Ubuntu to see the notebook and sd memory like just a single unit...its this posible and how if yes?TY

---

### Post by black veils on 2012-07-08
my guess is you would be best using Bodhi Linux, cant you just reinstall it?

---

### Post by BigMeme on 2012-07-08
> **black veils said:**
> my guess is you would be best using Bodhi Linux, cant you just reinstall it?
these linux distro:bodhi,puppy,peppermint etc always get broken on my "pc"...i found a way on the net for installing Ubuntu...In the past I installed and leeenux...Now I am thinking using Gparted and with that sd card,in terminal is posible:
-sudo apt-get install lampp '-path':'onSDMemory' 
and work ?
sorry for english....

---

### Post by ajgreeny on 2012-07-08
> **black veils said:**
> my guess is you would be best using Bodhi Linux, cant you just reinstall it?
I agree!

I think you are right on the edge for space with any of the standard *ubuntu family, as you can see from my df command on my machine with all of the various mixes of *ubuntu and Bodhi on a second disk used to test OSs.
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    9.9G  4.5G  4.9G  48% /
/dev/sda2     ext4    139G  101G   31G  77% /home
/dev/sdb5     ext4    9.3G  2.0G  6.9G  22% /media/Bodhi
/dev/sdb7     ext4    9.5G  4.3G  4.7G  48% /media/Lubuntu
/dev/sdb8     ext4    9.5G  6.0G  3.0G  68% /media/Ubuntu
/dev/sdb6     ext4    9.6G  4.4G  4.8G  49% /media/Xubuntu
```
Bodhi takes only 2GB for the OS, but the *ubuntu OSs all take 4.7GB or more.  OK, I could get rid of some stuff on the *ubuntu systems to reduce their size, but as a general point I think you can see what I mean.

---

### Post by Old_Grey_Wolf on 2012-07-08
I think you will probably have to install on the 32GB SD Card and use the eeePC's SSD as a data partition.

I had an eeePC 4g. I installed 8.04, I think, with / on the eeePC's SSD and /home on a SD Card; however, I doubt that will work any longer. I think / is going to be to big for modern versions of *buntu.

You could put /var, /tmp, /usr, and /home partitions on the 32GB SD Card; however, you are going to waist a lot of precious space making those partitions.

---

### Post by BigMeme on 2012-07-09
Finally after few hours of google-it,i will give up on any Linux,and choose Windows 7(after installing will be remaining 1.4 GB free) -with programs instalation on the SD card...this I think is better after results on searching...

---

