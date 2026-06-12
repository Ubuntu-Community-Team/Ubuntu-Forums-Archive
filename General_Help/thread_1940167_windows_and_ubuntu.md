---
title: "windows and ubuntu"
date: 2012-03-13
forum: General Help
---

### Post by adstri on 2012-03-13
Hello guys, ubuntu beginner here. 

My laptop is running ubuntu and i wish to change my desktop to it as well, when I try to do this i am running into a few issues. I have windows installed on a 2tb drive in a 200gb partition. The other partitions on the disk are windows recocery. Another 200gb partiorion that I wish to leave clear. And the remaining.which I would like to be the /home folder. 

Swap and / will be installed on secondary drive 60gb ssd. 

When i come to installing ubuntu off an ISO disk. Written at 8x speed slowest I could write it. Load up as a live desktop go to install and i cannot see any of the partitions that exist of either of the drives. If i look in disk utility I can see the drives with the partitions. Anyone know how I can install in the desired locations as I cant view partions in the installer?


After experiencing this issue I told ubuntu to install onto the ssd alone in the hope to get it running and more the home folder at a later date when i needed the space. This install gets right to the end then a fatal error occurs 'install-grub' fails. Any ideas how i can stop this from failing? 

Ideally the best fix would be to get Linux to recognise the partions so I can install it as planned. Please help would ideally like to have it running by this evening as i have work thay I need to do 


Thanks 
Adam :)

---

### Post by Mark Phelps on 2012-03-13
To give us a look at the formatting of your drives, please open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).

If you can't boot into Ubuntu on your hard drive to do this, then boot from an Ubuntu desktop CD instead.

---

### Post by adstri on 2012-03-13
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5201cb08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   419432447   209612800    7  HPFS/NTFS/exFAT
/dev/sda3       419432448   838862847   209715200    6  FAT16

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004e8fd

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 


This is what I get when I run the command as above in terminal. Hope you can help ? Or that the trained eye will make something of this! Sorry about the late reply. I have also added images of that i see in the disk utility

Thanks 
Adam

---

### Post by papibe on 2012-03-13
(responding to your PM)

I've never encountered a message like that, so I'm not sure what to suggest.

Regards.

EDIT: Researching a little makes me want to ask you this:

Was that disk used in another computer?
Was that computer a Mac by any chance?

---

### Post by adstri on 2012-03-13
The disk was used to run windows very briefly it was then reformatted for the Ubuntu install. After doing some research it appeared the best option was to install windows first then Ubuntu but these errors where encountered, since more googleing and looking around on forum I have had no luck. 

Thank you for looking into this, if you know of anyone who might have any ideas please point them in this direction :) 

Adam

---

### Post by papibe on 2012-03-13
Could post a screenshot of the disk using gparted on the live CD? ('try Ubuntu' instead of 'install')

Regards.

---

### Post by adstri on 2012-03-13
If I try doing try something else when in the installer I get the following:
Look at the disk partitions it shows that both are just free space with no partitions on them. 

Hope this is what you where looking for? The Disk utility is the only other option I can think of to show that they are partitioned and that the installer isn't seeing this at all, which is v. confusing.  Screenshot wouldn't save so that I could upload it apologies. 

Do you think it is a good idea to try formatting both drives using the disk utility option when running Live off CD then trying an install: 

/ filesystem on SSD
/ swap 8GB on SSD
/home 1.4TB on 2TB drive

I am really trying to avoid losing windows as reinstalling everything takes so long. The Ubuntu file system and settings once it is installed I can copy straight from my laptop :) 

Adam

---

### Post by Bucky Ball on 2012-03-13
I'm wondering if perhaps it was formatted as dynamic disk. Ubuntu doesn't understand these and can spit all sorts of odd predicaments and errors.

---

### Post by adstri on 2012-03-13
How would I find out if this is the case? Sorry for my lack of knowledge 

Adam

---

### Post by grahammechanical on 2012-03-13
How did you create these partitions and how did you format them? If you used Windows to format them, then they would now be dynamic disks because this is what happens now when you use windows to format a partion on a disk.

[http://technet.microsoft.com/en-us/library/cc731274.aspx]("http://technet.microsoft.com/en-us/library/cc731274.aspx")

Regards.

---

### Post by adstri on 2012-03-14
Thanks for the reply. I did format the drives in the windows inataller, anyone know what my next step should be then? 
 
Edit: Upon further reading of the link you sent me it appears that windows would only format the drives as dynamic if the partition was to span across multiple drives? I am fairly sure that i didnt make the drive have a dynamic partition not sure how I could confirm this though? 
 
Should I use the disk utility in ubuntu format both drives and start over?

---

### Post by oldfred on 2012-03-14
When you totally install Ubuntu to a drive somewhere over 1TB it automatically uses gpt not MBR as the partitioning scheme. But you only have to have gpt if drive is over 2.2TB. The arch site also recommends gpt for SSDs. But Windows will only work with gpt if you are booting with UEFI, so if dual booting with Windows and booting with BIOS you have to use MBR. And only the Windows drive has to be MBR. Windows 7 will read gpt data drives. My XP does not read my gpt drives.

When you install Windows with BIOS mode and a gpt drive, it converts to MBR, but only partially. GUID(gpt) keeps a backup of the partition table. Windows only overwrites the primary and never sees the backup. But Linux tools see the backup and get confused on whether it is MBR or gpt.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

Are you booting in BIOS or UEFI mode?

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD

Issues with OCZ Vertex II SSD and discard option
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by adstri on 2012-03-14
Thank you for all the information OldFred system is now up and running thanks to fix disk tool! 

Thank you to everyone else who helped with this issue 
Adam

---

