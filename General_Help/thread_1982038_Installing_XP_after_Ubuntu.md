---
title: "Installing XP after Ubuntu"
date: 2012-05-17
forum: General Help
---

### Post by chrgjen on 2012-05-17
Hi guys.

Here is an easy question. (I hope)

I have created af seperate partition (nfts) on my harddrive via LiveCD and wan't to install Win XP there. I have been researching guides and totorials to discover something called GRUB. Apparently I need to have SuperGRUB installed in order to properly boot Ubuntu and Win XP. So I found a SuperGRUB iso somewhere and now im stuck. 

Do I need to simply burn this image to a CD and use it after installing Win XP on my partition? Also. Do i need it every time I boot? (I can't imagine)

See I want to play Diablo 3. I tried Playonlinux install but too much lag and won't log in propperly. So an XP install seems logical.

Thanks :D

---

### Post by jtarin on 2012-05-17
This procedure will depend on if you partioned your XP to be before or after the Ubuntu partition. XP likes to be on the first partition.

---

### Post by layers on 2012-05-17
No need to read all the stuff about finding grub. (you can, if you want to know)

Just install XP. That will automatically "hide" your Ubuntu.

Then load an Ubuntu Live CD, install Boot Repair, and fix it with it. (it's very easy GUI)(sudo apt-get install)

edit: the comment about XP liking the first partition - not sure how true that is, but it definitely wants to be on a primary partition, not extended)

---

### Post by oldfred on 2012-05-18
Supergrub is a repair tool, Boot-Repair is a repair tool. Both are good or you can manual replace the grub2 boot loader in the MBR of your drive.  Just be sure to make a Ubuntu liveCD of your current version and make sure it works. Or download either or both of the repair tools and make repairCDs. I have all of them (and others) on CDs or USB flash drives just in case I need one or the other.

When you install Windows it will install its boot loader to the MBR. To install Windows you have to have a primary partition (sda1 thru sda4) formated NTFS with the boot flag.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

