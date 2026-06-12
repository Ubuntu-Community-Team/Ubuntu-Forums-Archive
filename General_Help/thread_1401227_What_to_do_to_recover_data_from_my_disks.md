---
title: "What to do to recover data from my disks?"
date: 2010-02-07
forum: General Help
---

### Post by Pernig on 2010-02-07
Hi, I'm browsing on my phone which is not letting me scroll to the end of this text box so I will say thank you in advance for any replies now.

After my computer was switched off abruptly after a power outage I have many errors upon booting. My hard drive setup consists of a RAID0 array of two 500GB sata disks. The partition table (from my head!) goes like this:

50GB NTFS Windows XP /c/
50GB ext4 Ubuntu 9.10 /
4GB swap
The rest is a large NTFS partition all the way up to the end of the array at 987GB. Mounted at /media/share/

I am thinking I will have to start again (I won't lose much, I have recent backups), but what is the best way of restoring the system as much as I can? Currently my computer has been booted into Ubuntu for over an hour, and after pressing ctrl+alt+shift+F2 I can see that it is finding errors still, now at sector 6008. Should I let this run its course or REISUB it and boot onto a live CD. I think the main problem is with an NTFS partition, so perhaps I should boot into XP and run chkdsk?

---

### Post by Pernig on 2010-02-09
I have solved the problem now. 

At first, I ran into a bit of a brick wall as XP would not boot to run chkdsk on the partition. Also, the XP install CD does not contain RAID drivers for my motherboard, and I have no floppy drive to load the drivers on Windows setup so I could not use Recovery Console!

I ended up making a streamlined XP disc using nLite, with the SATA RAID drivers included. It took quite a while to scan the partition and fix errors but chkdsk appears to have fixed all errors. :D

---

