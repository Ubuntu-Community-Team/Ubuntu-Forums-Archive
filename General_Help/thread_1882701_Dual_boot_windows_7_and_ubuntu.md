---
title: "Dual boot windows 7 and ubuntu?"
date: 2011-11-17
forum: General Help
---

### Post by ramus313 on 2011-11-17
so i have ubuntu 11.04 i think, and i would like to set up a dual boot with windows 7, i have windows 7 32 bit on a external hard drve... its a long story, bit will it be possible to dual boot from the hard drive, or should i put it on a disk? also, how would i go about doing this... there are a lot of tutorials from going from windows to ubuntu, but i have not seen any from ubuntu to windows. Sorry if i sound like an idiot, i am still very new to ubuntu..., i just need to dual boot for school related compatibility issues (I have wine, but it doesnt really work that great...)

---

### Post by tartalo on 2011-11-17
If in a terminal you write:```
sudo update-grub
```
Does it recognize the Windows in the external drive?

---

### Post by Mark Phelps on 2011-11-18
You said you have Win7 on an external drive, but are you actually able to run it from there?

Asking ... because the consensus in the Windows 7 forum is that running Win7 from an external drive is not possible!

---

### Post by elliotn on 2011-11-18
> **Mark Phelps said:**
> You said you have Win7 on an external drive, but are you actually able to run it from there?

Asking ... because the consensus in the Windows 7 forum is that running Win7 from an external drive is not possible!

yes I wonder how he made it

---

### Post by ramus313 on 2011-11-19
> **tartalo said:**
> If in a terminal you write:```
sudo update-grub
```
Does it recognize the Windows in the external drive?

no it does not, but i dont have it in the external harddrive anymore, i have it saved as an iso file on my computer, can i just mount the iso file? i cant find a way to do it though...

---

### Post by KingYaba on 2011-11-19
> **ramus313 said:**
> no it does not, but i dont have it in the external harddrive anymore, i have it saved as an iso file on my computer, can i just mount the iso file? i cant find a way to do it though...



You'll need to burn that Win 7 DVD iso to a DVD. You will also need to partition your hard drive so you can install Windows 7. You must also know that the Windows loader thing does not play nice and will stop you from using GRUB so you'll have to reboot (again) and reinstall GRUB using an Ubuntu live CD after you installed Windows. Your process will look something like this:

-Burn an Ubuntu Live CD to a CD (if you haven't already)
-Burn Win 7 to a DVD (if you haven't already)
-Restart your computer and boot up using the Ubuntu disc
-Use GParted to make a partition on your hard drive
-Restart the computer with the Win 7 DVD in and boot up the installer
-Install Win 7 on that newly-created partition
-Once Win 7 is installed, you'll need to put your Ubuntu CD back into your computer and boot up that live session to reinstall the GRUB bootloader.

---

### Post by ramus313 on 2011-11-19
> **KingYaba said:**
> You'll need to burn that Win 7 DVD iso to a DVD. You will also need to partition your hard drive so you can install Windows 7. You must also know that the Windows loader thing does not play nice and will stop you from using GRUB so you'll have to reboot (again) and reinstall GRUB using an Ubuntu live CD after you installed Windows. Your process will look something like this:

-Burn an Ubuntu Live CD to a CD (if you haven't already)
-Burn Win 7 to a DVD (if you haven't already)
-Restart your computer and boot up using the Ubuntu disc
-Use GParted to make a partition on your hard drive
-Restart the computer with the Win 7 DVD in and boot up the installer
-Install Win 7 on that newly-created partition
-Once Win 7 is installed, you'll need to put your Ubuntu CD back into your computer and boot up that live session to reinstall the GRUB bootloader.

so there isnt a way to do this without burning the windows 7 to a disk? i already have ubuntu on a disk, but i ran out of blank ones, so is there any other way?

---

### Post by KingYaba on 2011-11-20
> **ramus313 said:**
> so there isnt a way to do this without burning the windows 7 to a disk? i already have ubuntu on a disk, but i ran out of blank ones, so is there any other way?

There may be ways to install Windows using a flash drive but a DVD is what I used and thus what I recommended.

---

### Post by Mark Phelps on 2011-11-21
If you were to go to a Windows 7 forum (sevenforums.com, for example), you would find that there are several ways to install Win7 from an ISO -- but they all require you to be running Windows to do it -- because the install program is a Windows app.  Thus, AFAIK, there is no way to run that app from inside Ubuntu.

You will have to either burn the ISO to a DVD, or do the same to a USB stick of sufficient size (8GB) -- and install from that.

---

### Post by alphaamanitin on 2011-11-21
I think I once got a Windows 7 DVD iso onto a USB drive and booted from it simply by unpacking the iso with winRAR.  WinRAR is available on ubuntu.  anyway, this may have only been because I was using UEFI booting.  Cannot remember, cannot state with 100% certainty that the above statement is true.

AlphaA

---

