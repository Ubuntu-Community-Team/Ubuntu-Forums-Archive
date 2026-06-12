---
title: "Script to shrink partition"
date: 2010-09-22
forum: General Help
---

### Post by Toxlz on 2010-09-22
Hey guys.

I'm quite new in the linux world, just so ya know =P

Well... I've been givin this task, to make a script that shrinks the /dev/sda1 partition...

generally my scripts is working.. it just destroys all data on the sda1 partition when it gets shrinked... i still dont get why =P

You see... i have to shrink the partition sda1 ( with ubuntu 10.04.1 ), but with the installation intact, through a script...

I boot via the ubunto live cd, use my script, and my new partition sda3 is created perfectly as ext4.

But as i mentioned earliere, data is lost on sda1

My script :
#!/bin/bash
clear
umount /dev/sda1 ( just to be sure )
resize2fs /dev/sda1 14G
fdisk /dev/sda < commands
partprobe /dev/sda
./Myscript2

Myscript2 :
#!/bin/bash
partprobe /dev/sda
fdisk /dev/sda < commands1

Command file : deletes the sda1 partition and recreates it
Command file 2 : Makes the new partition for sda3

All this work fine if sda1 is just an empty ext4 partition, but bugs up if i have installed ubuntu on it...

Help Wanted ^^

---

### Post by bodhi.zazen on 2010-09-22
See if this link helps :

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641") 

It is for encrypted partitions, but it will walk you through the necessary steps and you should be able to adapt.

---

### Post by Toxlz on 2010-09-22
I have booted from the live Cd and install lvm2... Yet lvdisplay shows nothing...

Any ideas ?? =)

---

### Post by bodhi.zazen on 2010-09-22
> **Toxlz said:**
> I have booted from the live Cd and install lvm2... Yet lvdisplay shows nothing...

Any ideas ?? =)

If you are not using a crypt or LVM, you will need to skip those parts.

---

### Post by BobVila on 2010-09-22
This isn't a trivial task. I'd be afraid to trust any useful data to a script. Do you HAVE to script it? If not, a livecd with gparted/qtparted might be the way to go.

As far as destroying data, you're not attempting the resize while the disk is mounted, are you?

---

### Post by Toxlz on 2010-09-23
I have to script it, cause they want to make the resize automatic...
it needs to be done on 40+ computers...

I'm also a big fan of doing it with Gparted live cd, or Ubuntu live cd, cause its fast and works well tbh.. =)

No no... im not attempting the resize while the disk is mounted.. All the things i try i'm doing from a live cd =)

But so far i haven't been able to resize without the loss of Data :/..

Gparted does it very well, and i was wondering what command lines it uses for that task ?! ( im curious )

---

### Post by john newbuntu on 2010-09-23
At some point you mention that "Command file : deletes the sda1 partition and recreates it".  Well, right there you are wiping out sda1.  Instead you need to resize your partition properly.  And please bullet-proof your script well before trying it on other machines.  You could use parted for CLI.

---

### Post by Toxlz on 2010-09-23
Well... how to resize it properly then ??

and im working on the bullet-proof part... thats why im here asking for help =P

So far i know... Parted does not yet support ext4 ?! =)

---

### Post by Toxlz on 2010-09-28
C'mon guys... =)

Someone must know something ;)

---

