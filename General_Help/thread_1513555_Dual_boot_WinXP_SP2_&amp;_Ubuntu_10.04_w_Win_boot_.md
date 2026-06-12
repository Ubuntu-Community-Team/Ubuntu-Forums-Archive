---
title: "Dual boot WinXP SP2 &amp; Ubuntu 10.04 w Win boot loader"
date: 2010-06-19
forum: General Help
---

### Post by jamesegreen on 2010-06-19
I have a simple problem that I believe should be easy to solve.  I had WinXP SP2 installed on the primary partition of my C: boot drive and Ubuntu 9.10 installed on a primary partition of another large drive.  I set up to boot WinXP-32, WinXP-64 and Ubuntu 9.10 to boot using the Windows boot loader on the primary partition (I want to use the Win boot loader for good reasons).  
   
  To make Ubuntu boot, I used something like the following command to get the GRUB boot loader onto my C: drive boot partition: 
  dd if=/dev/hdaX of=/mnt/osshare/ubuntu.bin bs=512 count=1
  And copied ubuntu.bin to my C: drive.  Everything worked very well and all booted fine.
   
  Then Ubuntu 10.04 came out, I downloaded and burned the install disk, and upgraded the large disk to Ubuntu (with my Win drives unplugged).  I did the same dd command, copied the ubuntu.bin file the same as before, but Ubuntu won’t boot.
   
  I suspect that the new GRUB2 needs a bs=nnn file length different than 512 for the old 9.10 GRUB?  Can anyone tell me what this is, or what to do?

---

