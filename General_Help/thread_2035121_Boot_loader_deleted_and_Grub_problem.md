---
title: "Boot loader deleted and Grub problem"
date: 2012-07-29
forum: General Help
---

### Post by sinoka56 on 2012-07-29
I recently unistalled the ubuntu partition and I forgot to reinstall the windows boot loader and when I boot from USB with a flashdrive with ubuntu 12.04 installed I get an error with GRUB 

Help please D:

is there a way to reinstall windows boot loader without a Windows CD or install again ubuntu? :)

---

### Post by oldfred on 2012-07-30
If you have a Windows repairCD or USB you can use it.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


You can use this which you can install to an Ubuntu liveCD or download as a liveCD:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Or from an Ubuntu liveCD:

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by sinoka56 on 2012-07-30
I don't have ubuntu 12.04 anymore on my hard drive can I use Ubuntu Live ? To reinstall the boot loader? :)

---

