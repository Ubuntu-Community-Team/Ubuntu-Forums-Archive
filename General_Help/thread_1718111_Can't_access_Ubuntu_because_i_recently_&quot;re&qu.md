---
title: "Can't access Ubuntu because i recently &quot;re&quot;installed windows"
date: 2011-03-30
forum: General Help
---

### Post by tanuace on 2011-03-30
about 6 months ago I installed Ubuntu because my Windows XP had been partially corrupted and was screwing up. One month ago I formated the drive XP was on and installed Windows 7 Home Premium 64bit on it; I couldn't dual boot so I looked online, found EasyBCD 2.0, installed it, and from what I can tell, I need GRUB on my Ubuntu side to be able to boot it, before this I didn't even know what GRUB was. I have absolutely no idea what to do...

---

### Post by dhjohnson on 2011-03-30
Are you sure that Ubuntu is still there and that Windows didn't overwrite it when it was being installed?  I believe that may be what happened.

---

### Post by seawolf167 on 2011-03-30
Take a look [here]("https://help.ubuntu.com/community/WindowsDualBoot"), scroll down to the section "Installing Windows after Ubuntu" and see if the instructions listed help you be able to dual boot again.

[Here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") are the instructions on how to install GRUB2 from a LiveCD

---

### Post by tanuace on 2011-03-30
> **dhjohnson said:**
> Are you sure that Ubuntu is still there and that Windows didn't overwrite it when it was being installed?  I believe that may be what happened.

I cant find the partition it is on from my windows side, but I used an Ubuntu 10.10 loader disk's "try Ubuntu" option and it was fully intact as far a I could tell.

---

### Post by tanuace on 2011-03-30
I figured it out, Grub 2 is already on Ubuntu 10.10... I almost can't believe it was that simple...

---

### Post by seawolf167 on 2011-03-30
> **tanuace said:**
> I cant find the partition it is on from my windows side, but I used an Ubuntu 10.10 loader disk's "try Ubuntu" option and it was fully intact as far a I could tell.

The "Try Ubuntu" loads the Ubuntu image from the CD/DVD onto you computer to use in a "Live Environment". This is not actually an installed partition - anything you do here will not be saved for a future boot.

I think what the previous poster meant was if you right-click "My Computer" then select "Manage" then "Disk Management", if there a partition on your disk (that Windows can't read) that belongs to Ubuntu? Otherwise the reinstall could have used your entire disk and overwritten Ubuntu.

---

### Post by tanuace on 2011-03-30
> **seawolf167 said:**
> The "Try Ubuntu" loads the Ubuntu image from the CD/DVD onto you computer to use in a "Live Environment". This is not actually an installed partition - anything you do here will not be saved for a future boot.

I think what the previous poster meant was if you right-click "My Computer" then select "Manage" then "Disk Management", if there a partition on your disk (that Windows can't read) that belongs to Ubuntu? Otherwise the reinstall could have used your entire disk and overwritten Ubuntu.

What I meant was, I found the partition that Ubuntu was on fully intact, not that I thought that the "try Ubuntu" was my partition. but, I figured out my problem and this post is coming from my Ubuntu partition.

---

