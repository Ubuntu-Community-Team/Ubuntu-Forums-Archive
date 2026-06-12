---
title: "Problems booting back to vista"
date: 2010-01-01
forum: General Help
---

### Post by Tumblweed on 2010-01-01
I'm having a problem I had vista on my system,installed ubuntu but let the installer partition the drive,
+0now every time I try to boot to windows it has to do a system restore to boot. any advice as to where to start to find the problem? btw both seem to run fine once booted.

---

### Post by Leppie on 2010-01-01
what do you mean with "system restore"? does it go into a recovery system which then re-installs windows to the factory defaults?

---

### Post by Tumblweed on 2010-01-01
No,it has the gray box saying windows is trying to repair my system then it says windows is reverting back to a early time,after a few min  it reboots I have to tab down to boot normally and it does

---

### Post by Leppie on 2010-01-01
> **Tumblweed said:**
> No,it has the gray box saying windows is trying to repair my system then it says windows is reverting back to a early time,after a few min  it reboots I have to tab down to boot normally and it does

are you sure this isn't a virus issue? doesn't sound at all like a problem caused by installing ubuntu.

---

### Post by Tumblweed on 2010-01-01
Pretty sure,unless the viri was on the iso i downloaded from ubuntu's site(avg dosent see a viris).dl it made the disk and installed.not sure but I have the feeling something is changing my boot record between ubuntu and vista and they dont seem to want to agree on what it should be.but I have no idea nor any idea how to check it.

---

### Post by Tumblweed on 2010-01-01
Btw would I not be able to see the ubuntu partition from within windows explorer? just like i see the "recovery partition" as another drive.

---

### Post by Leppie on 2010-01-01
> **Tumblweed said:**
> Btw would I not be able to see the ubuntu partition from within windows explorer? just like i see the "recovery partition" as another drive.

windows is not able to see non-windows partitions.

---

### Post by Leppie on 2010-01-01
> **Tumblweed said:**
> Pretty sure,unless the viri was on the iso i downloaded from ubuntu's site(avg dosent see a viris).dl it made the disk and installed.not sure but I have the feeling something is changing my boot record between ubuntu and vista and they dont seem to want to agree on what it should be.but I have no idea nor any idea how to check it.

is avg on the windows system?
you may want to try some other scanners (maybe even try an online one?).

if windows is restoring to a previous state every time you boot it, that pretty much sounds like a virus/malware issue.

---

### Post by Mark Phelps on 2010-01-01
> **Tumblweed said:**
> I'm having a problem I had vista on my system,installed ubuntu but let the installer partition the drive ...

THIS is most probably the culprit.  Letting the installer partition the drive runs the risk of corrupting the Vista OS filesystem. There are lots of posts on this forum about NOT allowing the Ubuntu installer to shrink Vista -- guess you didn't see them.

The most common fix for this is to boot into Vista using a recovery CD (not an OEM restore CD) and do Startup Repair several times.  That will remove GRUB from the MBR, so you'll have to restore that as well.

---

### Post by Tumblweed on 2010-01-01
> **Mark Phelps said:**
> THIS is most probably the culprit.  Letting the installer partition the drive runs the risk of corrupting the Vista OS filesystem. There are lots of posts on this forum about NOT allowing the Ubuntu installer to shrink Vista -- guess you didn't see them.

The most common fix for this is to boot into Vista using a recovery CD (not an OEM restore CD) and do Startup Repair several times.  That will remove GRUB from the MBR, so you'll have to restore that as well.
 
Unfortunately no I didn't see them till after the fact when searching the forums I found that,that is why i had the feeling it was the culprit,ill restore and rewrite the mbr  and try a viri scan online to see if one of those helps. Thanx to all for the help 

and yes avg is on the windows partition,just dl'd avg for the Linux partition.

---

### Post by Leppie on 2010-01-01
> **Tumblweed said:**
> and yes avg is on the windows partition,just dl'd avg for the Linux partition.

try other av's as well. clamav is in the repos. there's also fprot, avira, etc.  for linux.

---

### Post by Tumblweed on 2010-01-01
> **Leppie said:**
> is avg on the windows system?
you may want to try some other scanners (maybe even try an online one?).

if windows is restoring to a previous state every time you boot it, that pretty much sounds like a virus/malware issue.
just to be clear it only restores to previous state after i boot to ubuntu,not when i shut down from windows or reboot

---

### Post by Tumblweed on 2010-01-02
Update. I deleted the partition for ubuntu via windows,reinstalled ubuntu,but i messed up something in setup somehow it made yet another partition while setting up instead of putting it on the one i via windows,so now windows has a even smaller partition.I tried installing avg on ubuntu it says its there but cant find it to run so cant test for virus's.still does same thing.but I did some trials and seems i don't have to restore....from grub i select boot to windows,get the Microsoft splash screen......black screen then grub.....select windows get the splash screen........black screen then it says error recovery and "windows didn't load correctly i either have to select repair"recommended" or boot normally,if i try to boot normally it will show splash screen.....grub..select windows...splash screen then finally boot up windows. and that's every time I try to boot back to windows after running ubuntu.
this is extremely confusing for my already confused mind....lol.I did download the book [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/) ill do some reading.any ideas on what might be going on or what to look at would be appreciated

---

### Post by Leppie on 2010-01-02
I would suggest to remove the ubuntu installations from within windows (go to control panel and open add/remove programs). If you still have files in the first ubuntu installation, copy them over to a safe place. Then check the size of your windows partition, and if there's any free space (i.e. unpartitioned space) left on the disk.
Then reboot and boot with the livecd and reinstall ubuntu.

---

### Post by Tumblweed on 2010-01-03
> **Leppie said:**
> I would suggest to remove the ubuntu installations from within windows (go to control panel and open add/remove programs). If you still have files in the first ubuntu installation, copy them over to a safe place. Then check the size of your windows partition, and if there's any free space (i.e. unpartitioned space) left on the disk.
Then reboot and boot with the livecd and reinstall ubuntu.
Its not there to uninstall,just gonna give up for now and do some more studing I cant even get the simple commands to work correctly[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142233&stc=1&d=1262500106[/IMG]
gonna restore system to factory settings and try again after i do more reading.thanx for all that tried to help.

---

