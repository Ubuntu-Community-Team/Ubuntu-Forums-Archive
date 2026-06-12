---
title: "Loading OS error on startup, unknown filesystem"
date: 2012-09-23
forum: General Help
---

### Post by Drew012 on 2012-09-23
I have an SSD with Windows 7/Ubuntu 12.04 on it. I had some serious problems with Ubuntu after a while which required a fresh install. I used the Windows utility to delete the Ubuntu partition and then use my USB flash drive to reinstall ubuntu. However, after deleting the partition (it was empty space which I changed to NTFS format). I get this message on start up...

Loading Operating System...
error: unknown filesytem.
grub rescue>

What do I have to do to fix this, I can access BIOS but not even my Windows partition.

---

### Post by Bashing-om on 2012-09-23
Drew012; Hi ! welcome to the forum.

Be advised ..one cannot run ubuntu (linux) on partitions formated for windows (ntfs) [use as data partition, yes]....soooo
My recommendation:       others may offer better =>
  windows tools for windows' problems, linux tools for ubuntu situations.
Windows rescue cd to restore windows bootloader, chkdsk to verify system files integrity.
Windows disk management utility: delete the erroneous ubuntu partition, Leave the space unallocated (for ubuntu tools to use in install later). While you are in the windows disk utility: check how many primary partitions windows is using..... "older" operating systems can only have a maximum of 4 primary partitions per hard disk. I am more comfortable installing ubuntu onto it's own primary partition (windows taking up to three).

 When the above is accomplished,, then install ubuntu:
in the installer routine choose to install along side of; the installer will format and install on the former free space. Bootloader: ubuntu's grub will default install to sda and chainload windows, giving you the option as to which os to load.

Feel free to respond to any instance you do not understand. We are here to help.[INDENT]happy ubuntu'n <==BDQ

[/INDENT]

---

### Post by varunendra on 2012-09-24
I'd like to add just one more thing to whatever *Bashing-om* said above. There is a very handy GUI tool - [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), which can fix most of the common booting issues automatically (of course after asking your permission). If not, it can create a boot-info summary which can help us a lot to understand the problem and troubleshoot it accordingly.

So before trying anything else, please download & install it (on a live session running off a live cd) and run it to see if it can fix your problem.

---

### Post by Drew012 on 2012-09-24
Thanks for the help guys but I have tried both solution and nothing has worked. I am able to load the disk tool but it did not fix the problem when I did everything in the GUI. I also have tried booting in to Ubuntu off of a live flash. I am using Unetbootin too, and that part load up. Under the unetbootin menu there are two of each option listed (ex: Install Ubuntu, Install Ubuntu, Boot Ubuntu without installing, Boot Ubuntu without installing). However there is only 1 "default" option. No matter which option I choose, the bar gets stuck highlighted on that answer and it looks as if it was trying to load something, but nothing happens. Right now I am trying to gparted live bootable flashdrive but it seems like it get stuck while loading on the system.

---

### Post by Drew012 on 2012-09-24
UPDATE: I just tried using the live usb with the iso file deployed by unetbootin, and it worked...On my other computer... 

This means something in my settings is not letting me boot off of the USB properly on the one computer. Any ideas on what this could be? I tried messing around with a few things I am comfortable with in BIOS but it had no effect. I also tried to set it BIOS to default settings but it still would not work.

---

### Post by YannBuntu on 2012-09-25
Hello

> **Drew012 said:**
> I am able to load the disk tool but it did not fix the problem when I did everything in the GUI.

Please click "Recommended repair" and indicate the URL that will appear.
(don't use Advanced options if not asked).

---

