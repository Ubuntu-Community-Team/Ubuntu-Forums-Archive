---
title: "reinstalled windows on a dual boot. Grub issue"
date: 2012-07-23
forum: General Help
---

### Post by Alphamonkey on 2012-07-23
Hi, I have a computer where I was multi booting windows, ubuntu, and fedora. My windows partition crashed so I reinstalled. After doing so I can no longer see my grub boot menu. I was wondering if I need to reinstall grub, and if so how, or if there is a better easier solution that is available. Thanks.

---

### Post by oldfred on 2012-07-24
If it is grub2.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

You can also do it manually from an Ubuntu liveCD. ONce in Ubuntu you have to add the lvm2 driver if you have not and mount the Fedora partition for grub2's os-prober to find the Fedora install.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Sandertje on 2012-07-24
You will indeed have to re-install grub. The windows bootloader, which is installed together with windows itself, does not see any other OSes than windows itself (Micro$oft doesnt want you to use any other OS? :P).

Therefore, in general, it is better to install Ubuntu (or any other linux distro) after you've installed windows on dual-boot systems.

---

### Post by oscarivera9 on 2012-07-24
What you mentioned happened to me once because I had problems with Windows 7 and had to use the Windows 7 install disc to repair a problem.  As Sandertje said, Windows likes to think that there aren't any other operating systems besides Windows, so it is very greedy and re-installs its bootloader onto the MBR without any respect to other operating systems.
  Follow oldfred's advice, he's an expert when it comes to this sort of thing.
 Also, keep in mind that you want to use a Live CD from the same Ubuntu release that you have installed, it's just better that way.  It makes it so that it gets the correct Grub2 version installed.

---

