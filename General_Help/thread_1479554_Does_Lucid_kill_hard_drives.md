---
title: "Does Lucid kill hard drives?"
date: 2010-05-10
forum: General Help
---

### Post by Jerry N on 2010-05-10
I had an IDE hard drive failure while trying to install a Lucid beta.  Gparted wouldn't touch it.  I finally booted from a DOS floppy and removed all partitions with FDISK, then repartitioned and formatted it successfully.  On a different computer, I installed the Lucid release version on an SATA drive from an alternate install disk.  It installed but after about the 4th restart it turned off the computer during the boot process.  Several times.  Again, Gparted thinks it is a bad drive and Windows doesn't recognize it as a working drive. I am currently running Lucid on another computer with no failures yet.  Has anyone else had what looks like a hard drive failure after trying to install Lucid?  I think I am afraid of Lucid now!  I have more drives but the supply is finite.

Jerry

---

### Post by bondo101 on 2010-05-10
> **Jerry N said:**
> I had an IDE hard drive failure while trying to install a Lucid beta.  Gparted wouldn't touch it.  I finally booted from a DOS floppy and removed all partitions with FDISK, then repartitioned and formatted it successfully.  On a different computer, I installed the Lucid release version on an SATA drive from an alternate install disk.  It installed but after about the 4th restart it turned off the computer during the boot process.  Several times.  Again, Gparted thinks it is a bad drive and Windows doesn't recognize it as a working drive. I am currently running Lucid on another computer with no failures yet.  Has anyone else had what looks like a hard drive failure after trying to install Lucid?  I think I am afraid of Lucid now!  I have more drives but the supply is finite.

Jerry         I had some of the same problems with the sata hard drive i'm using now for lucid. I tried loading XP on it first windows wouldn't reconize the drive , then a format then i loaded linux 9.10 on the drive and all was fine after running for a day or so it asked if i wanted to upgrade so i did , no problems yet . I ran drive test in lucid found out I had some bad sectors in it . Today still running fine on old hp parts machine that i re did , for linux box.try an old version  see if it will load . Windows i'm tired of .

---

### Post by efflandt on 2010-05-10
Could it have something to do with the new partition alignment used by 10.04?
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems](http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems)

I installed 64-bit 10.04 LTS on part of a 500 GB USB drive, which booted fine on 2 laptops, but failed to boot on my desktop.  So I figured I would try it on a 160 GB USB drive that I know has no problem booting 64-bit 9.10 on my desktop.  10.04 on that drive booted fine on the laptops, but not on my desktop.

Apparently I have an Asus motherboard that cannot handle the new 10.04 partition alignment.  So I used 9.10 to recreate the partitions on the 160 GB drive and used the **partman/alignment=cylinder** boot parameter for the 10.04 install CD, and was then able to boot the USB drive from my desktop.  So I used that boot parameter to boot a USB iso and successfully installed 64-bit 10.04 LTS to a partition on my main desktop hard drive (which formerly had 32-bit 9.10).

My desktop PC that originally had a problem with 10.04 is an HP a530n w/ASUS K8N8X-LA HP/Compaq motherboard name: Diablo-UL6E, Athlon64 3200+ @ 2 GHz running its original 200 GB hard drive since 2004.  I am posting this from 64-bit 10.04 LTS on that.

---

### Post by igf1 on 2010-05-10
I also installed lucid and had a drive die... how odd. I doubt it's actually the partitioning though. My drive went south during the beta. So the drive was all ready partitioned... after one of the updates my puter started spouting ascii at me in some really odd places. Then the drive manager informed me that "failure was eminent" and that was all the motivation I needed to get that new SSD I've been eying. Which I was just about to post a How-To on. ;)

---

### Post by Jerry N on 2010-05-10
This is a rather disappointing situation.  My first failure was on an older Shuttle motherboard with an Athlon2400+ processor while the second was on a Gigabyte motherboard with a dual core Athlon 3800+ processor.  I have done a lot of Windows installations from 3.0 through 7 (skipping ME and Vista) without any problem like this and, being a incurable tinkerer, at least 50 linux installations (mostly on the Athlon 2400+).  **I think I will give up completely on 10.04.**  I definitely won't install it on my new PhenomII primary computer - Win 7 and XP do the job just fine.  As I type, I am installing 9.10 on my secondary machine, which also runs XP and Win 7 quite well.

Jerry

---

### Post by Jerry N on 2010-05-11
> **efflandt said:**
> Apparently I have an Asus motherboard that cannot handle the new 10.04 partition alignment.  So I used 9.10 to recreate the partitions on the 160 GB drive and used the **partman/alignment=cylinder** boot parameter for the 10.04 install CD, and was then able to boot the USB drive from my desktop.  

Question 1:  If you partition and format the drive using 9.10, is it really necessary to use any special boot parameters for installing 10.04 **IF** you don't format the drive during install?

Question 2:  Where and how do you invoke the **partman/alignment=cylinder** boot parameter?

Jerry

---

### Post by dbowlin17 on 2010-05-11
i had a new install, then recently upgraded copy of lucid. it killed itself while sleeping. sad, never knew computers could kill themselves... reinstalled 9.10 and moved on. lucid sucks balls. the end. i used aplha 3 and it was better than lucid final release. thats not how it is supposed to work...

---

### Post by Jerry N on 2010-05-11
> **dbowlin17 said:**
> i had a new install, then recently upgraded copy of lucid. it killed itself while sleeping. sad, never knew computers could kill themselves... reinstalled 9.10 and moved on. lucid sucks balls. the end. i used aplha 3 and it was better than lucid final release. thats not how it is supposed to work...

Maybe I will just wait for 10.04.1 before I try this Lucid again.  What happened to you is basically what happened to me on my first install of the released version.

Jerry

---

### Post by dbowlin17 on 2010-05-11
yeah. actually it happened after i installed 10.4 clean i think. i dunno. soo many times reinstalling this weekend. 10.4 had no usb for me. by 10.4 i mean 10.04

---

### Post by Worp8d on 2010-06-17
I'm losing sectors progressively on my 1TB Seagate.  I thought it was the drive but now I just repartitioned my laptop and the install crashed after very nearly completing.  Is progressive hard drive failure a symptom of the problem described here, or is it something else?  The laptop is old and daily abused and would have good reason for failure itself so I'm not sure if I should start backing up my stuff?  (Guess I just should anyway)

---

### Post by philinux on 2010-06-17
[http://www.pcworld.com/article/129558/study_hard_drive_failure_rates_much_higher_than_makers_estimate.html](http://www.pcworld.com/article/129558/study_hard_drive_failure_rates_much_higher_than_makers_estimate.html)

[http://www.pcmech.com/article/hard-drive-failure-warnings-and-solutions/](http://www.pcmech.com/article/hard-drive-failure-warnings-and-solutions/)

You all had me checking my smart data. Guess I'll go do a backup. :mrgreen:

---

### Post by gandalf2000 on 2010-06-21
I, too, have had a drive begin to die.  It is a Western Digital 1 Tb that is less than a year old and had no trouble until after I went to Lucid.  It has my /home on it and I have bought a new drive to replace it so I can send it away.  Just need to figure out how to get them changed over.  Any ideas?

---

