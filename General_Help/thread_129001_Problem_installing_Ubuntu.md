---
title: "Problem installing Ubuntu"
date: 2006-02-12
forum: General Help
---

### Post by Kamakzie on 2006-02-12
I installed Ubuntu after I ran Partition Magic and made a new 30 gig partition.  Once the install was about complete it asked me if I wanted to install Grub I selected NO!  I ran into problems trying Grub before...  It asked if I wanted to install it to another drive or a floppy.  I wrote in /dev/fd0 and my floppy drive ran and it said complete.  So it said to remove all cd's and floppy's and reboot.  I removed the cd but kept the floppy in.  The computer rebooted and the floppy kicked in and said GRUB.  That was it, nothing it just sits there.  I rebooted to windows and examined the floppy and there is nothing written to it....  Like its freshly formatted.  Whats the deal?  Help!!!!!!!  :D

---

### Post by Robgould on 2006-02-12
I did not even know you could do that.  I have never had any issues with grub though.  I'm giving this a little bump.  I'm curious about this myself.

---

### Post by Kamakzie on 2006-02-12
Hmmmm well see I have a SATA boot drive for windows.  I had the misfortune of installing GRUB to that to try and dual boot between Ubuntu and WinXP and it hashed the drive so it wouldn't boot anything.  It gave me a invalid OS error.  So I just got WinXP back up but would really like to try Ubuntu.  I made a 30 gig partition on an old IDE drive.  So one part is NTFS on one partition while the other partition is Linux.  Can I install Grub on the IDE drive without destroying the NTFS portion of the drive?  I realize that when I would want to boot to Ubuntu I would need to enter my BIOS and make the first boot as IDE instead of SATA.  I wouldn't mind doing that but I don't want it hurting the NTFS data or screwing with my SATA boot record again..

---

### Post by Kamakzie on 2006-02-13
Okay now I am really perplexed.  I decided to try and install Ubuntu on another IDE drive.  I have Ubuntu automatically configure the partition.  The large partition is set as / and the swap is set to /ext3.  I made a backup of my windows installation and told Ubuntu to install GRUB to my SATA boot drive which is where Ubuntu detects my windowsxp install.  Unfortunately it installs GRUB to HD0 which is NOT my XP drive.  So after installation it just boots right back into windows...  What am I doing wrong?  During the partition faze it shows my SATA drives as SCSI and the XP drive is listed as /dev/sda but during the GRUB install I tried to manually put /dev/sda as the install directory and it gave me errors...  UGH!  :(

---

### Post by cotcot on 2006-02-13
If i understand you well you have XP on the SATA and you want to install Ubuntu on the IDE.
You can install Ubuntu on the IDE and install grub to /dev/fd0 instead of the MBR. 
So you keep the XP bootloader on the SATA, no bootloader on the IDE and the grub boot loader to the floppy. This setup works by me except that i have 2 IDE disks. 
Normally you should have the files "stage1" , "stage1_5", "device.map", "menu.lst" on your IDE under /boot/grub. The grub bootloader on the floppy loads these files. If you do not have these files it will not work.
I can confirm that you do not see anything on the floppy with the grub boot loader. Actually the bootloader is only less than 512 bytes.

---

### Post by Kamakzie on 2006-02-13
Hmmm I tried that before and it just said Grub during the bootup but it went no where...

---

### Post by Kamakzie on 2006-02-15
Finally got it to install using Ubuntu 6.04.  It let me use /dev/sda for GRUB.

---

