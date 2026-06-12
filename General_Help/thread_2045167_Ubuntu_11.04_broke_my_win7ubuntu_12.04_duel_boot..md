---
title: "Ubuntu 11.04 broke my win7/ubuntu 12.04 duel boot."
date: 2012-08-20
forum: General Help
---

### Post by Ninjax on 2012-08-20
I've been using Ubuntu 12.04 for several months now. For one of my college courses I was suppose to install Ubuntu 11.04 from the CD that came with the book. I had a bad feeling about trying to install it since I already have Ubuntu 12.04 installed. I popped it in and restarted then selected "install Ubuntu." This caused the installer to crash and said there was an unexpected error. Tried to reboot and now my computer hangs on start up and appears to be trying to access a server or something. Now the only way I can get my computer to boot is by inserting the Ubuntu 11.04 CD and selecting the "Boot from first drive" option. How can I fix my system boot files also how can I do a triple install of Ubuntu 12.04, Windows 7, and Ubuntu 11.04? Do I have to create another partition?

---

### Post by oldfred on 2012-08-20
Welcome to the forums.

I always prefer to create partitions in advance as then I have control over sizes. The auto installs just try to repartition as best as they can, but you may or may not have some control over sizes.

I use 25GB for / (root) but keep data in other partitions so I can share the data. If dual booting with Windows you should have a shared NTFS data partition and set the Windows system partition as read only.

This should let you reinstall the grub2 boot loader from your 12.04.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

If primarily booting with 12.04 the Something Else or manual install also gives you the choice on where to install the grub2 boot loader. I would install it to the / partition as a throw away. Normally you do not install grub2's boot loader to a partition, but since booting with the 12.04 version, you have to as there is not an option not to install grub. Then in your 12.04 run this and it will add your 11.04 to the grub menu.

sudo update-grub

---

