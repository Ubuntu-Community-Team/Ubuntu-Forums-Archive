---
title: "Windows 7 + Ubuntu Dual Boot 2 *seperate* drives."
date: 2011-05-01
forum: General Help
---

### Post by destrugter on 2011-05-01
Hello everyone, I am new to Ubuntu and had a question about installing it. I've used it once before but got fed up with the boot asking me everytime I turned my laptop on because I wasn't using it enough. Anyway, here is my question.

I have Windows 7 on drive C . I want to keep it on drive C. I have several 1.5TB+ drives, and one of them is not being used. I want to dedicate it to Ubuntu, and be able to do a dual boot with my Windows 7 install. Is this possible? If it is, what about when this drive is not connected to my laptop? Will that mess up the boot process? Please let me know =)

---

### Post by destrugter on 2011-05-02
Bump. (Fell to 28th page in like...no time at all?!)

---

### Post by Quackers on 2011-05-02
During the installation you just need to make sure that grub bootloader is installed to the mbr of the Ubuntu hard drive. As it will default to /dev/sda (which is the first hard drive on the system) you need to change that drive to your Ubuntu drive's name. It may be /deev/sde or /dev/sdf, for instance. Find out with gparted from the live cd desktop.
At the partitioning stage of the installation there is a box at the bottom of the screen headed "device for bootloader installation" (if you are using Ubuntu 11.04). This is what would need to be changed.
When that's done and the installation is complete you will need to make the Ubuntu hard drive bootable before any other hard drives, in your bios.
If you do it this way your other operating systems should boot normally when the Ubuntu hard drive is not attached.

---

