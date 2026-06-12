---
title: "recover data from dead ubuntu"
date: 2011-01-02
forum: General Help
---

### Post by lindberg.bill on 2011-01-02
I reinstalled windows on a partition of my hard drive and lost my grub boot loader so I cannot get my ubuntu to work.  Try as I might I cannot reinstall grub.  I just don't understand all the terms and procedures.  All I want to do now is get the contents of my home folder onto a usb and reinstall.  I have a bootable persistent usb Kubuntu I boot in and navigate to the home folder of my dead Ubuntu and find that I cannot access the contents because it can not be mounted.  Is there a way to get these files? Is there a way to use my persistent usb Kubuntu to install grub?

---

### Post by Rubi1200 on 2011-01-02
What have you done to try and reinstall GRUB?

As long as the partition is there, it should be a simple procedure.

See here:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

Post the results of the boot info script linked at the bottom of my post so we can see what is going on.

Thanks.

---

### Post by MadnessRed on 2011-01-02
Do you get any error messages when you try and mount the partition?
How are you trying to mount the partition?

If that doesn't work, perhaps try [ext2read](http://sourceforge.net/projects/ext2read/) from windows. You may be able to copy the files onto you usb that way.

---

