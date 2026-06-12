---
title: "Numerous Problems Booting"
date: 2010-02-14
forum: General Help
---

### Post by RockHero on 2010-02-14
I'll start with the basics:

The computer that I'm dealing with is a whitebox computer that I did not configure.
I first allocated 50gb of the unformatted HDD for Karmic Koala, then installed it. I had trouble with it because the computer has an ATI video card, and there was a ton of problems trying to get it to work with no sucess. I have recently installed Windows 7 onto it, but I had to install it with the HDD inside of another computer because it would not install on the whitebox computer.

Now on to the main problem: (i've fixed a few problems since ive posted this thread)
Grub does not show Windows 7 at all

Lesser problem:
I would love to get the ATI card to work so that I can do fancy things with Compiz

Side notes:
This is the 64bit version
I can access my Windows partition through Ubuntu

fdisk -l:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49c3bd0a

___Device_____Boot__________Start__________End__________Blocks_____Id___System
/dev/sda1_____________________1_________6565________52733331_____83___Linux
/dev/sda2______*___________6566________13577________56320000______7___HPFS/NTFS
/dev/sda3_________________13577________60802_______379330560______7___HPFS/NTFS

---

### Post by flippo on 2010-02-15
Grub2 is the karmic boot loader, all the info you need for that can be found here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Proprietary video drivers are always fun, here is the community documentation:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you have any issues just post them, although I'm not very familiar with grub2.

---

### Post by RockHero on 2010-02-15
Well, the documentation on the ATI drivers helped. I got the driver to work, but I still cant use compiz.

And the Grub2 information didn't really help with my problem.

---

### Post by ironclaw on 2010-02-16
In Ubuntu, run
```
sudo update-grub
```
to update your GRUB configuration to include the Windows installation. GRUB should automatically detect Windows and add it as an option to /boot/grub/grub.cfg.

---

