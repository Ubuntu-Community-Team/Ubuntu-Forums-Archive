---
title: "Install slackware without blank dvd from ubuntu?"
date: 2010-08-21
forum: General Help
---

### Post by Dustin2128 on 2010-08-21
I was running slack 13, and I want to upgrade to 13.1 via a fresh install. However all of my blank dvds are irreparably scratched, and I'm more worried about scratches on an OS install disk than I would be otherwise. I have the ISO downloaded and my disk partitioned (via gparted on knoppix live). I'm ready to go, I just need to figure it out. I don't have a flash drive available with more than 4GB of storage space so unetbootin's out.

---

### Post by Dustin2128 on 2010-08-21
I'd really like to know how to do this because I have googled it, and every *single* tutorial was for windows as the preinstallled OS.

---

### Post by corrytonapple on 2010-08-21
Did you try this in virtual box?

---

### Post by Dustin2128 on 2010-08-21
> **corrytonapple said:**
> Did you try this in virtual box?

No, I don't have any vms at the moment.

---

### Post by andrew.46 on 2010-08-27
Hi Dustin,

Perhaps this is what you are after:

A Slackware Desktop Enhancement Guide
Installing Slackware Without a CD Drive
[http://humanreadable.nfshost.com/sdeg/installing_no_cd.htm](http://humanreadable.nfshost.com/sdeg/installing_no_cd.htm)

Andrew

---

### Post by Mateuszk on 2011-02-01
Is there possibility to install Slackware as a second OS parallel to Ubuntu from ISO? Mabye I will explain more...

I have Laptop with Ubuntu. I want to try Slackware, but unfortunatelly I have connection to web by WiFi. If I start installing Slackware from DVD I would not have internet connection so  there will be no possibilty to download some additional packages. Moreover it will be hard to install drivers for wireless without web. Unfortunately at the moment I do not have possibilty to connect with router by ethernet (wifi only). :/ That why I want to install somehow SLackware from Ubuntu. Ofc I knew about virtual box but I want to install Slack on another partition and I want to boot it from lilo or other booting manager.

Best,
Mateusz

---

### Post by bodhi.zazen on 2011-02-01
See the above link, it has step-by-step instructions. 

The DVD will have everything you need to do the installation.

If you have a problem, please ask in the Slackware forms =)

---

### Post by tam2tam on 2011-02-01
Hi Mateuszk,

I currently have both Oses on my system. Most of the packages you require to get slackware up and running are on the installation disk. Slackware is rock solid but installation is done with a minimal GUI.

Make sure you partition your hard disk and make sure you know which partitions you want to install Slackware on. Mine is sdb4 for instance. You need three partitions generally. One for root, 10 gigs should suffice. One for swap double your memory size is the norm. the rest for your data (mine is /home).

You will not boot into the GUI straight away. Suggest you read the slackbook before installing. You will have to configure your system to start the x server by editing inittab in directory /etc.

linuxqusetions is the place to go to help, do a search before asking questions as the answer probably will already be there. I have not configured wireless, but there are plenty of posts on how to do that.

Tot get info and download any packages needed you can do so in ubuntu. All drives will be available in both slackware and ubuntu. So download to place on an ubuntu partition. boot back into slackware and locate the file and copy it from ubuntu to a place in the slackware partition.

Slackware is not for the faint hearted. Be prepared for headaches, but patience will be rewarded. It is worth it.

---

### Post by Habitual on 2011-02-03
[Install any Linux distro directly from hard disk without burning any DVD]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html")

---

### Post by andrew.46 on 2011-02-14
> **tam2tam said:**
>  Slackware is rock solid but installation is done with a minimal GUI..

The installation screens will be a little familiar to those who have ever installed Ubuntu using the 'alternate' cd, a little different...

---

