---
title: "how can I run gparted on ubuntu 9.10"
date: 2010-04-17
forum: General Help
---

### Post by mjsilverstri on 2010-04-17
Hi,

How can i rung 'gparted' on ubuntu 9.10?
I tried 'sudo gparted', and I look for it in 'System->Administration'. But both doew not work.

---

### Post by Jlb181 on 2010-04-17
Is it installed?  Silly question I know, but it should be in your Administrator menu.  If not, use the Ubuntu software center to install it.

---

### Post by mjsilverstri on 2010-04-18
Yes. I have installed it

> 
sudo apt-get install gparted 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



---

### Post by Serpher on 2010-04-18
It's under a different name. I think it's "Disk Management" or something like that. Also in terminal, if you type in an application name it'll run it like this:

$gparted


Although you'll probably need root privileges so

$gksu gparted

---

### Post by mjsilverstri on 2010-04-18
Thank you. I tried 'gksu gparted'. It asked me for my password. But nothing happened, no other window pop up.

---

### Post by wilee-nilee on 2010-04-18
It is called gparted check your menu edit right click on menu hit edit and see if it is in system-administration and needs to be ticked off then on to get it to show, this happens at times. If it isn't there look in synaptic and see if it is actually installed. worse case google gparted download the ISO burn a copy. Also gparted wont mess with a live running OS in case you don't know this, also a live CD of Ubuntu has gparted on it already.

---

### Post by mjsilverstri on 2010-04-18
I have it installed. But some how, I can't launched it.

> 
sudo apt-get install gparted 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by wilee-nilee on 2010-04-18
You can try a reinstall so run sudo apt-get purge gparted the sudo apt-get install gparted

---

### Post by mjsilverstri on 2010-04-18
Thank. This works.

---

### Post by wilee-nilee on 2010-04-18
> **mjsilverstri said:**
> Thank. This works.

Good news.

---

### Post by coffeecat on 2010-04-18
@mjsilverstri, if by chance you want to create or work on NTFS partitions in Gparted, you also need to install the package ntfsprogs. This is available in the live session, which is why you can create/shrink NTFS partitions with the live CD, but does not get installed when you install to your hard drive. This confuses a lot of people when they find that the NTFS option is greyed out in Gparted in their permanent installation.

---

