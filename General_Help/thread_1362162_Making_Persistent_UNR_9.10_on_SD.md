---
title: "Making Persistent UNR 9.10 on SD"
date: 2009-12-22
forum: General Help
---

### Post by ck472006 on 2009-12-22
Hi all, im kinda new to ubuntu. Recently, i tired making my SD card to run Ubuntu Netbook Remix by installing it on my computer with HDD taken out. But it crashed after a while as it formats my SD to NTFS rather than FAT32.

I was wondering if anyone could make a guide on how to make a live USB Ubuntu Netbook Remix 9.10 where i can save changes and updates. So that i could dual boot XP and UNR 9.10 on my Benq Joybook Lite U101W.
BTW, teaching me how to Fully Install UNR 9.10 on the SD card would be best.

Thx in advance

---

### Post by omskates on 2010-01-20
From a live 9.10 CD use GParted to format your SD Card to EXT3 or EXT4. Click manage flags and select "Boot".
Go through the full install process choosing the SD card as target drive, installing to entire drive.
I'm not sure if "USB Startup creator" applies to SD but that will give an option to leave the drive persistent.  
Using GParted to pre format the SD Card should solve most issues.

---

### Post by C.S.Cameron on 2010-01-20
You should be able to remove your HDD plug in your SD then boot from the Live CD or a Live USB.
Run "Install Ubuntu" from the second screen, (the one after language choices). 
When you get to Partitioning you can select "use entire disk" or select "Manual".
Default file system for 9.10 is ext4 but you can also select ext3.

For a full install the SD should be at least 4GB.

---

