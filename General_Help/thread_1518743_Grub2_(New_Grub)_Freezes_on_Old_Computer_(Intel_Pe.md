---
title: "Grub2 (New Grub) Freezes on Old Computer (Intel Pentium III + Asus P3B-F)"
date: 2010-06-27
forum: General Help
---

### Post by XP1 on 2010-06-27
**Grub2 (New Grub) Freezes on Old Computer (Intel Pentium III + Asus P3B-F)**

--

Yesterday and today, I spent several hours trying to install Ubuntu 10.04 (from Live CD, Live DVD, and Alternate CD), Xubuntu 10.04 (from Alternate CD), and Lubuntu 10.04 (from Live CD).
It took a few hours of installing for each different combination above.
On a few occasions, the installation froze, so I tested the 3 RAM sticks. 1 RAM stick had multiple failures in the Windows Memory Diagnostic test. I then removed all RAM except one 128MB stick, which had passed the test.
I continued trying to install Ubuntu on 128MB RAM. However, each time the installation is done and restarts, the computer goes through its BIOS stage and then after that, it freezes at a blank black screen. The keyboard does not respond (NUM LOCK key is frozen and CAPS LOCK does not work), and the hard drive activity light is off.

--

Next, I tried to figure out what the problem was. I installed Ubuntu from the Alternate CD again using the _[partman/default_filesystem=ext3]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes")_ boot parameter.
However, the computer still froze at a blank black screen.

Finally, I burned Puppy Linux 5.0.1 onto a CD and booted it up. I went to **Menu > Setup > Grub ...** to reinstall Grub. Next, I mounted **/dev/sda1** and went to **.../boot/grub/** to view the Ubuntu setting. I then noticed that Ubuntu's Grub wasn't using the **.../boot/grub/menu.lst** file, so it must be a newer version.
By then, Grub was reinstalled and the **.../boot/grub/menu.lst** file was created and set to defaults.
I opened the new **grub.cfg** and translated the Ubuntu setting into the old **menu.lst** file.
I rebooted the computer and after the BIOS, the old Grub shows up and then I can finally boot Ubuntu!

--

[s]This only half works, however. When I shutdown, the computer freezes at this screen (the Ubuntu loading screen imposed over the screen output):[/s]
[INDENT]```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161672&stc=1&d=1277622262[/IMG]
```See "_[Ubuntu doesn't shut down completely. My computer stays on.]("http://ubuntuforums.org/showthread.php?t=521540")_".[/INDENT]

--

Some questions:
[LIST=1]
[*]Does anyone know what is going on with the Grub2 setup?
[*]Why does the old computer freeze on Grub2?
[*]How can I fix this freeze on Grub2?
[*][s]What else can I do to fix the freezing on shutdown?[/s] See "_[Ubuntu doesn't shut down completely. My computer stays on.]("http://ubuntuforums.org/showthread.php?t=521540")_".
[/LIST]

--

Quick Specs:
> CPU: Intel Pentium III, 550 MHz (5.5 x 100)
Motherboard: Asus P3B-F (4 DIMM); Intel 82440BX Chipset
Video: S3 Graphics Inc. Savage4 (32 MB)
RAM: 128MB to 320 MB (SDRAM)
Hard Drive: FUJITSU MPE3170AT (16 GB, 5400 RPM, Ultra-ATA/66)
Optical Disc Drive: ATAPI CD-R/RW 6X4X32 (6x/4x/32x CD-RW)
Ethernet: 3Com 3C900B-TPO Ethernet Adapter
Modem: U.S. Robotics 56K Voice Win 1806
Audio: Creative SB PCI128 (Ensoniq ES1371) Sound Card

--

[B]Links of Possible Interest:
[LIST]
[*]Webpage on Low-Memory Systems:
_[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)_


[*]HowTo: Revert from grub2 to Legacy Grub.
_[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)_


[*]Ubuntu doesn't shut down completely. My computer stays on.
_[http://ubuntuforums.org/showthread.php?t=521540](http://ubuntuforums.org/showthread.php?t=521540)_
[/LIST][/B]

---

### Post by XP1 on 2010-06-27
Here's what I did so far:

I removed the "splash" from the **/boot/grub/grub.cfg** file. It did not work.

Next, I compared the UUIDs from **/boot/grub/grub.cfg** and **sudo blkid**. They were the same. The **/etc/fstab** file did not have any UUID for sda1 (only UUID for swap).

I also tried "Unhide/Hide the Menu" _[here]("http://ubuntuforums.org/showthread.php?t=1302743")_, but it did not work.
I also tried setting the grub2 resolution to 640x480:

Then, using _[http://ubuntuforums.org/showpost.php?p=9513124&postcount=8](http://ubuntuforums.org/showpost.php?p=9513124&postcount=8)_ from Lubuntu 10.04 Live CD:```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
sudo update-grub
```

It still freezes after BIOS. :confused:
Also, holding [SHIFT] displays a "Loading Grub...", clears display, and then freezes at a blank black screen.

---

