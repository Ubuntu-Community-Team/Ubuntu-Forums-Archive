---
title: "Grub/boot menu help"
date: 2012-08-31
forum: General Help
---

### Post by dudeman4566 on 2012-08-31
I haven't ran Ubuntu since 10.04 and was dual-booting with Vista. I recently decided to upgrade both. The problem is that my boot menu still says Vista and Ubuntu 10.04 when it is really suppose to be 7 and 12.04. The normal solution of what I've done in the past was use the command  /etc/default/grub and edit it in the text file. For some reason when the text file opens up it is blank.....and I also checked in  file /boot/grub for the "grub.cfg" file but it isn't in the folder. I am really puzzled and just want to simply edit/rename the grub menu. Any help would be great. I installed the grub-customizer program but don't seem to understand how to rename or work it. 

-thank you

---

### Post by oldfred on 2012-09-01
I have not used grub customizer, but it should let you rename all the grub entries.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you want to confirm what is installed where or just document system, run the BootInfo report and post link it creates:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

