---
title: "Asus Eee 701 &amp; SD Card"
date: 2009-11-11
forum: General Help
---

### Post by MES5464 on 2009-11-11
I just installed the Ubuntu Netbook Remix on an old 4GB Asus Eee Netbook. Everything seems to be working fine with one exception. Ubuntu doesn't notice the 16 GB SD card in the reader. I have checked the "sudo fdisk -l" and the dmesg, etc. I have tried the card in my other laptop runing Ubuntu 9.10 and it sees it just fine. I have been all over the internet and seen instructions to manually mount the sd card by editing /etc/fstab and then mounting the card (plus some other suggestions), but nothing seems to work. Assuming that the SD card reader is working, what more can I try to get the SD card to mount and stay mounted?

---

### Post by Maringouin on 2009-11-12
I just installed 9.10 UNR on my Eee PC 901. During the install, I realised I had forgotten to take out the SD card; the install read it as a FAT32 formatted drive and asked me to label it for use as a partition.
I'm not very skilful with Ubuntu so I just followed all the default options; UNR is installed and working fine (except for Picasa :-() but the SD card doesn't show up as an available drive.

Running 'sudo fdisk -l' gets the following:


Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd643d643

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         490     3935893+  83  Linux

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux

Disk /dev/sdc: 8017 MB, 8017936384 bytes
202 heads, 59 sectors/track, 1313 cylinders
Units = cylinders of 11918 * 512 = 6102016 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1314     7825920    b  W95 FAT32


I can access the disk through the Palimpsest Disk Utility, where it looks as in the attached screenshot. The drive is identified as J:

8.0 GB / 7.5 GiB / 8,013,742,080 bytes
FAT (32-bit version) File System
Partition 1 (W95 FAT32) (0x0b)
/dev/sdc1 mounted at /windows

'/windows' is a hyperlink and when I click on it, I can access the card and all the material on it, even run music and videos from the card.

How do I make the 'drive' visible?
Other important question: does this configuration mean I can't change the card? I was planning to upgrade to a 16GB card soon.

Thanks. I'm not very skilled at Linux but can follow clear instructions like a champion.

---

### Post by MES5464 on 2009-11-12
I think you are going to have to redo the install. Right now I think your Eee is using a SD card as a part of the OS. If you take the card it I think it would stop working. I would just start over.

My problem is different from yours. I can't get my Eee to even see the SD card is there.

---

### Post by Maringouin on 2009-11-12
Marion, I'm not sure I need to do the reinstall. I could just delete the partition in Disk Manager, I think. But want to check my options first. It doesn't bother me a huge amount because I use the card mostly for storage and I can still access it. I have a long way to go before it's filled up.

Have you checked this thread about sd cards?
[http://ubuntuforums.org/showthread.php?t=958750]("http://ubuntuforums.org/showthread.php?t=958750")

And thanks for your comments!

---

### Post by MES5464 on 2009-11-12
> **Maringouin said:**
> 
Have you checked this thread about sd cards?
[http://ubuntuforums.org/showthread.php?t=958750]("http://ubuntuforums.org/showthread.php?t=958750")


Yes. I looked at that one. The problem is the very first step. When I fdisk -l the SD card doesn't show up at all. That is why I can manually add it to the /etc/fstab file.

---

### Post by supermaurio on 2009-11-12
I finally found out!! You have to enter BIOS and set the "OS installation" to "finished".
Nothing else.. SD cards will show and mount automatically on a EEE 701

---

### Post by Maringouin on 2009-11-13
Glad you got that sorted out!
I'm going to move my inquiry to a new thread to see if anyone picks it up.
Good luck with your Asus! I love mine, have been using it non-stop as my only computer since I got it.
Best wishes,
Margaret

---

### Post by sgosnell on 2009-11-13
The card is visible, but not as a separate card.  In Nautilus, it will show as /windows.  You can use it as you would any other folder.  If you remove the card, it won't be mounted.  You can edit /etc/fstab to remove that mount point, and the card should then show up as a separate drive.

---

### Post by Maringouin on 2009-11-14
Thanks, sgosnell!
I checked as you said, and there it is.
Also I can access it as a folder called 'windows' through File System in the file browser window.
That's great--and I've filed away your advice for when I might want to change the card.
Thanks again!:D

---

