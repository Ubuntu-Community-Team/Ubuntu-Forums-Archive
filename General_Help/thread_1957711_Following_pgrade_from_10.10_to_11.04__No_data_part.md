---
title: "Following pgrade from 10.10 to 11.04  No data partitions visible"
date: 2012-04-13
forum: General Help
---

### Post by Engineeringtech on 2012-04-13
My system is not showing me my NTFS, FAT16, FAT32, and HFS+ partitions, following an upgrade from 10.10 to 11.04.  

I allowed the update manager to upgrade my machine. The update went smoothly and the only question I was asked during the process was if I wanted to keep my existing "local" boot config file.  Being a total novice, I said to keep the existing boot config file.

The installation completed, and my machine restarted.  A message popped up saying I was missing a certain file, followed by a command line prompt.  I think it was "Grub rescue:"  The reboot process stopped there.

I got my Super Grub 2 disk out, popped it into the machine, and let it boot me up.   When I got to the desktop, I used a program called "Boot Repair" to fix Grub.   I rebooted, and the machine got to the desktop, albeit lacking my desktop background picture.

My NTFS, FAT16 and FAT32 (Windows) partitions are not seen in the "Places" pulldown menu, or on the desktop.   I ran GPARTED, and the partitions are all there.    How do I get my partitions mounted, and listed in the "Places" menu?

Thanks for your time.

---

### Post by raja.genupula on 2012-04-13
give us the output of 
```
/etc/fstab
```

---

### Post by Engineeringtech on 2012-04-13
> **raja.genupula said:**
> give us the output of 
```
/etc/fstab
```

At work right now, I will get that for you as soon as I get home.     

Wanted to also state, that this is a dual boot system (Windows and Ubuntu) which has been booting and operating just great.   (I installed  Grub the way people here always recommend, to SDA, rather than another partition.

After I started this thread last night, I found out that my Windows partition no longer boots.  The error message I get is that "HAL.DLL" is missing.   I am guessing that this means the boot.ini file was screwed up or that Grub doesn't know where the partition is.  

Does the above information help you any?

Thanks

---

### Post by Engineeringtech on 2012-04-13
> **raja.genupula said:**
> give us the output of 
```
/etc/fstab
```

Here it is..  Sorry for the delay.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=2ab378ca-ec5b-491c-a1e2-29114fd43579 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6806ca9a-9dff-47ce-8f7e-3c58e34f7300 none            swap    sw              0       0
# /dev/sda5 /mnt/windows vfat fat32 defaults 0 0



Thought I would also attach a screenshot of my partitions from Gparted.  They're there.  I just don't know why I can't get to them.

---

### Post by raja.genupula on 2012-04-14
ok add these entry's and try again . 

```
/dev/sda1 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

/dev/sda5 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0
/dev/sda6 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0

/dev/sda9 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

```

add these at end of ftsab and try again

---

### Post by callmemahavir on 2012-04-14
Refer the following link for mounting NTFS, FAT32 and FAT16 partitions.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Also refer

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

LOT OF INFORMATION IS AVAILABLE THERE!!!.

---

### Post by Engineeringtech on 2012-04-14
Raja,

I hope I understand what you are doing here.. I didn't need to mount SDA6 (Windows swap partition), and I wanted more appropriate names on the other partitions, so I changed your code slightly.  On reboot, I found three icons on my desktop.  When I click on EITHER the Windows or DOS icons, BOTH icons flash, but the partition doesn't open up.   If I click on the Data icon, the partition opens correctly.  I can't dismount any of the three icons.  Could this have something to do with the dual entries for SDA5 in FSTAB?  Is the one  preceded by the # just a comment?  My DOS partition is FAT16, and the Windows partition FAT32.  Shouldn't this information be in your code?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc     nodev,noexec,nosuid                            0  0  
# / was on /dev/sda7 during installation
UUID=2ab378ca-ec5b-491c-a1e2-29114fd43579  /               ext4     errors=remount-ro                              0  1  
# swap was on /dev/sda8 during installation
UUID=6806ca9a-9dff-47ce-8f7e-3c58e34f7300  none            swap     sw                                             0  0  
# /dev/sda5 /mnt/windows vfat fat32 defaults 0 0

/dev/sda1                                  /media/DOS      vfat     defaults,user,exec,uid=1000,gid=100,umask=000  0  0  
/dev/sda5                                  /media/Windows  vfat     defaults,user,dmask=027,fmask=137              0  0  
/dev/sda9                                  /media/Data     ntfs-3g  defaults,locale=en_US.utf8                     0  0

---

### Post by Engineeringtech on 2012-04-14
> **callmemahavir said:**
> Refer the following link for mounting NTFS, FAT32 and FAT16 partitions.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Also refer

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

LOT OF INFORMATION IS AVAILABLE THERE!!!.

Thank you also.

---

### Post by Engineeringtech on 2012-12-29
I've finally marked this thread as "SOLVED".   My solution is to return to the "dark side" (Windows).  I made no progress with the problems for a very long time, and I need a computer I can USE.   I had wanted to stay with Ubuntu so much that I opened more than one thread on the problems, pursuing different approaches.   (I couldn't keep up with the advice)    I apologize for doing  that.    

Thanks to everyone for trying to help me with Ubuntu.

---

