---
title: "Grub 1.5 Error 17 when Dual Booting Vista and Kubuntu"
date: 2009-07-16
forum: General Help
---

### Post by AcousticMinja on 2009-07-16
So it seems I'm having quite a bit of trouble here at the moment. As the title states, I am getting the error "Grub 1.5 Error 17" when I start up my computer. I've tried these two solutions [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) and [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9) and it does not seem to be working for me or I'm just not doing it right. I'm not really sure what to do right now. On my first hard drive I have Windows Vista, and on my second hard drive on a partition on that drive I have Kubuntu 9.04. I checked device.map and it seems as my hard drives are in the correct order. I checked my BIOS and it shows the same. (my motherboard is an MSI. Not sure of the model number though).

So anyway, if anyone can please help me out here, it'd be much appreciated. I know there are several of these posts out there but like I said, I can't seem to be getting it to work or I'm doing it completely wrong(as I am a linux newbie anyway)




(edit) Now I have an even bigger issue. I decided that maybe if I deleted it Kubuntu from my hard drive I could just use Vista and install it again later when I figured it out correctly. I used Gparted to format the drive to an NTFS and deleted everything off of it. Now when I start up my computer I come to the same screen; "Grub 1.5 Error 22" is what I see now. Again, I searched online for it and now it said that I need to run some sort of thing in Windows RE. I don't have my Vista disc anymore...I lost it. Now on to my question, is there ANY WAY I can fix this Grub Error using my Ubuntu liveCD? I booted off of it right now and that's how I'm typing this.
Please help. I can't afford to delete my other hard drive with Vista on it.


(Edit 2) Here is some more information about how my partitions are set up.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80de80de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fb38fb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS


By the way, I really have no clue what I can do now. I've searched forums but people who have had error 22 didn't delete their other OS. 
I don't have any blank CDs or USB sticks to boot from to use fixmbr for Vista either. Is there a terminal command I can use?

---

