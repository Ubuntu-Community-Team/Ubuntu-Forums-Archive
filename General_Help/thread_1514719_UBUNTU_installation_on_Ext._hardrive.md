---
title: "UBUNTU installation on Ext. hardrive"
date: 2010-06-21
forum: General Help
---

### Post by Eastwood1 on 2010-06-21
[FONT=Arial Black]I have an 80 G hardrive occupied by XP. 50% available free. Used a CD  (Ubuntu 9.0 downloaded from internet) to install.Defragmented the harddrive before starting and checked files. Also have 300G Ext harddrive  (USB) occupied 33% with data including photos scans etc.[/FONT]
[FONT=Arial Black]Message found after trying to install Ubuntu: Not enough free space to install Ubuntu on harddrive, XP occupying 75% although 50% available. Unmovable files (green) found after defrag. at 1/2 way and 3/4 way mark on across harddrive with wide open spaces (free) inbetween. The only real free area is 5 gig at the end, not enough to install Ubuntu.[/FONT]
[FONT=Arial Black]How can I install on the external harddrive and still keep my data intact. How do I partition?[/FONT]
[FONT=Arial Black]Many threads have been posted but my problem still seems unique[/FONT]
[FONT=Arial Black]What now my love?:guitar: Please help this novice[/FONT]

---

### Post by Ampi on 2010-06-21
If you use the live CD from Ubuntu you can (without installing) open Gparted. In there you should be able to resize the partitions on the 80G or 300G hard disk, making the XP or data partition smaller and leaving enough space for Ubuntu. 
Even though, maybe someone else with a bit more idea than I could say something, because Ubuntu should be able to fit on even 25G, so I find it strange Ubuntu won't install, could be maybe a dual-boot issue.
If if does not work you could try to put the data together with your XP (for example on the 300GB) and then put Ubuntu alone (on the 80G) in a harddisk, you can still have a shared data partition for both XP and Ubuntu..

Good luck..

---

### Post by eriktheblu on 2010-06-21
A couple of options:
1. Find a better defragmenting tool. I have no idea if there actually is one, but might work.

2. Identify the offending file(s) and move them manually

3. Boot from USB:
   a. The live CD has an install to USB option from the live session
   b. You can do a normal full install to a USB disk, but this can cause problems with your internal disk's MBR. I recommend disconnecting your internal hard drive first to avoid any errors.

4. Boot from internal HDD, run from USB.
This would be a little complex, but that 5 GB at the end of your disk could be employed for part of your Ubuntu install. In the install, manually partition your disks. Allocate 256 MB at the end of your internal in an EXT4 (assuming 9.10 or above, otherwise EXT3 will work) file system, and designate it as /boot. With the remaining space, create a swap partition according to your needs. Resize the existing partition on the external, use the new space for / (I'd go with at least 15GB) and /home (according to your needs) partitions.

5. Reinstall Windows. This is probably the best option of all of these. When your file system gets to be that fragmented, it's time to start over. This should be a yearly habit with Windows.

---

### Post by K.J. on 2010-06-21
The unmovable files are one of two things, either virtual memory swap or the hibernation file.  Boot into windows and disable both, then try again.

---

