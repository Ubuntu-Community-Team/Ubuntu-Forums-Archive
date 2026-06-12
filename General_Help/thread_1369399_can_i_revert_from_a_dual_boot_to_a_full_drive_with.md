---
title: "can i revert from a dual boot to a full drive without reinstall?"
date: 2009-12-31
forum: General Help
---

### Post by eival on 2009-12-31
i have ubutu and windows as a dual boot, i no longer need the windows portion and could really use that space now.

i REALLY dont wanna reinstall Ubuntu even tho its not very complicated, but if i could simply run a few command codes an bypass that id love it.

or, im also wondering, if i chose to update from 8.04 to 8.10 or later, would it ask me if i want to use that additional space and keep all my files automatically?

---

### Post by dcstar on 2009-12-31
> **eival said:**
> i have ubutu and windows as a dual boot, i no longer need the windows portion and could really use that space now.

i REALLY dont wanna reinstall Ubuntu even tho its not very complicated, but if i could simply run a few command codes an bypass that id love it.

or, im also wondering, if i chose to update from 8.04 to 8.10 or later, would it ask me if i want to use that additional space and keep all my files automatically?

You just need to make sure Grub is installed on the Linux partition and not the Windows partition that you are going to delete.

It is a fairly simple process to reinstall Grub, just do a forum search for detailed instructions.

---

### Post by HappyFeet on 2010-01-01
Just use gparted froma live cd to resize the linux partition. If you need to reinstall grub after, that can also be done from the cd.

---

### Post by Ordes on 2010-01-01
how is your setup? (one hdd multiple partitions, different hdd`s for the OS, etc), what boot loader? 

Basiclly you can just format the windows partition. But if you want to merge the formated one with an existing one your hdd / partiton layout will change.. so u probably will need to fix the boot loader and fstab..

might wanna try remastersys.. you can make a liveISO from your distro with all the apps.. and than just reinstall your ubu after formatting your hdds... Is /home and / on different partitions? than you should have your OS running in 5 min after formatting...

---

### Post by eival on 2010-01-02
> **Ordes said:**
> how is your setup? (one hdd multiple partitions, different hdd`s for the OS, etc), what boot loader? 


i have 2 partitions on 1 hdd, i installed windows first, then ubuntu and it setup the grub boot loader automatically.

so i just wanna delete the windows os an add that space to ubuntu.

---

### Post by eival on 2010-01-02
> **HappyFeet said:**
> Just use gparted froma live cd to resize the linux partition. If you need to reinstall grub after, that can also be done from the cd.

well i found gparted in synaptic, i assume i could use it to do the same thing, rather than use the live cd?

heres how my system is set up

[http://i47.tinypic.com/mv0l6e.png](http://i47.tinypic.com/mv0l6e.png)

what steps would i need to do to merge the ntfs with the ext3?

do i just format the ntfs to ext3 and then merge and put the "boot" flag on sda5?

---

### Post by Ordes on 2010-01-03
Dont use gparted on system mounted devices like / . Always use the liveISO. If u just want to edit e.g sda1 it safe to do it from inside the system.

First Method:
1) Load up liveISO
2) delete sda1. 
3) resize sda2 extended to full size
4) resize sda5 (might need to unswap & delete sda6 first, resize sda5,create swap partition 4gb if deleted)

>> in this method your sda2 extended will stay as it is.
>> / and /home will still be one partition, which i think is not very good
>> perhpas u might need to reinstall grub.
>> There is no way to get rid of sda2 extended, without deleting sda5 & sd6. sda2 is like a container for them

Second method.
> When you already repartition, you could think about making a par for / and making a par for your /home.
> Has your linux system a lot of apps installed that it would be a hassle for your to install a fresh copy? Or are you basicly running the default ubuntu? 

> If you dont want to reinstall the apps etc from your system, than get remastersys. And make a liveISO from your system without /home. Second choice in the menu. Put it on a CD/ USB. Boot it up with live, to check if its working...
[http://geekconnection.org/remastersys/ubuntu.html](http://geekconnection.org/remastersys/ubuntu.html)

Use LiveISO (original or the remastersys one,)
1) Delete sda1
2) Resize sda2 to full size
3) create parition in sda2 for your system. around 10-15 gb (make primary)
4) resize sda5 to merge with the rest free space
5) a) mount your sda5
   b) delete all your "system" directories (e.g bin, boot, etc), except /home 
   c) rename your /home to /old-home
   you shouldnt need to do it... but to be on the safe side
   

>> now you should have sda2 [ sdaNEW (10gb), sda5 (134gb), sda6 (swap 4gb)
>> sda5 will be your /home.. and sdaNEW will be your / (system root)

6) go into the linux installer (use the Rem-Sys-ISO, if you want to install "your" system. When it comes to partiton setup choose manual
7) > sdaNEW edit > choose "/" (format)
   > sda5   edit > choose "/home"  (**DO NOT MARK FORMAT, otherwise your data is gone**
   > sda6   SWAP
8) In User-Setup make the same settings as u had before (username etc)

Finish setup and reboot. Your ubu wont have your old settings yet. As your new /home has not your files yet. In /home/old-home/username should be all your previous data

9) Move all your files (including hidden files) from /home/old-home/username to /home/username by command (check if the given paths from me are right, e.g /home/old-home/username)

sudo rm -r /home/username  

sudo mv /home/old-home/username /home/username

10) check permissions for /home/username.. or just run
$ sudo -R username:username /home/username

11) log out & in, and you should have your "old" linux, with seperated partitons for / & /home

12) if you installed a fresh ubuntu and did not use remastersys, now its the time to reinstall your apps

and u r done

PS; no matter if u use method 1 or 2. It is always good to have a data backup when editing partitions containing files. I never had a problem. And mostly there wont. But like last time my friend had a power black out during partitoning. It f**** him up pretty good....

---

