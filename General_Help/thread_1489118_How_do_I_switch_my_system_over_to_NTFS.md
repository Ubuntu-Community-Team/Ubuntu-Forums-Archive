---
title: "How do I switch my system over to NTFS?"
date: 2010-05-20
forum: General Help
---

### Post by Absolome on 2010-05-20
I need to change this laptop over to windows 7, but I can't unless it's NTFS, Someone said I could do this with a LiveCD or USB bootloader, help!

---

### Post by Dayofswords on 2010-05-20
what do you have currently on the laptop?

NTFS is a file system for windows and windows 7 is install on and saves files in it

do you know about partitioning?

---

### Post by efflandt on 2010-05-20
You could use gparted from a Linux CD to remove existing partitions (assuming that you backed up anything you want to save elsewhere).

Then Win7 install it should give you the option of formatting some or all of the drive as NTFS for itself, and it will install a regular Windows mbr to boot it.

---

### Post by ali999 on 2010-05-20
You can use the live version and load gparted to create a new NTFS partition. I have found gparted to be pretty good at resizing partitions and all that. 
I am assuming here that you are trying to set up a dual boot system. If you want just windows then simply put in the windows disk and format away.
Note: If you are dual booting, windows tends to write over the grub boot loader (if linux is installed first) so you need to restore that after. There are plenty of threads in this forum on that.

---

### Post by uRock on 2010-05-20
When I installed Windows 7 Pro, the partitioner could see the EXT partitions and had the option to delete them.

---

### Post by llamabr on 2010-05-20
Are you just trying to switch from ubuntu to windows 7?  Pop in the windows disk -- windows will format your disk for you.

---

### Post by ali999 on 2010-05-20
all you need to do is use gparted to resize the current ext partition. Then create a new one in the now freed up space and use that to install windows. Don't format the ext partition because then you will loose linux (unless you want to do that)

---

### Post by paydaydaddy on 2010-05-20
I recently converted a hard drive that was formatted with ext3 to NTFS so I could install windows7. The windows disc absolutely would not recognize the hard drive while it was formatted to ext3, even after deleting the partition. I burned gparted to cd, popped it in the cd tray and in less than a minute had the hard drive converted to NTFS. From there installing windows7 was a relative breeze. Finding and installing all the drivers (64 bit) took another two days. Then another 2 days to get networking with xp and kubuntu configured.

---

