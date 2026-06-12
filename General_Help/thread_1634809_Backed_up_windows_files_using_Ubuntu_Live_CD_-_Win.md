---
title: "Backed up windows files using Ubuntu Live CD - Windows can't see them."
date: 2010-12-01
forum: General Help
---

### Post by yensed on 2010-12-01
I offered to help a friends parents re-install windows XP on their 4 year old desktop. They have pictures and documents everywhere so I figured I would just backup their entire HDD onto my external one and let them go in and transfer them back off. I keep proper backups so this isn't how I normally do things. I have done similar things in the past with dieing HDD's and Knoppix but I have never had this issue. I burned a CD using the latest ISO and Ubuntu seen both the main HDD and my external. I just copied all the contents of the main HDD over to the external. All went well and I could browse and view all the files from the external HDD after the transfer using the live CD. Unfortunately I am having an issue seeing the external HDD in Windows. As soon as I hook the drive up - windows says I need to Format it(Which I won't do obviously). But if I boot the live CD I can still see and use the files. How do can I get windows to see the drive and files without destroying data? I have done Tons of searching but am getting nowhere. I would really appreciate the help.


-Dan

---

### Post by Jahid65 on 2010-12-01
I don't know about the windows , but you can use the live cd to do the reverse. copy-paste all the files from external HDD to Main HDD via live cd.

---

### Post by julio_cortez on 2010-12-01
> **yensed said:**
> so I figured I would just backup their entire HDD onto ***my*** external oneLet's start with a stupid question: is it NTFS or FAT/FAT32? I guess so (otherwise it's normal that Windows doesn't see it), but better be sure about that.
Does it actually get assigned a drive letter by Windows, or it's just stuck there being unrecognized?

The most easy thing to do should be using the Live CD to bring data back anyway, but I would then perform a check on that external disk (just in case) as it doesn't look like behaving properly if it's NTFS or FAT/FAT32.

---

### Post by runeh76 on 2010-12-01
hmm if u used linux live-cd to copy data... I think that live-cd change ur files permission or maybe better to say change ur files to Linux file system "read only in linux" and thats why windows doesnt recognize that. Try another bootable software.

By the way i didnt understand so well.. Did u went their machine and put ur hd in?

---

### Post by COKEDUDE on 2010-12-01
> **yensed said:**
> I offered to help a friends parents re-install windows XP on their 4 year old desktop. They have pictures and documents everywhere so I figured I would just backup their entire HDD onto my external one and let them go in and transfer them back off. I keep proper backups so this isn't how I normally do things. I have done similar things in the past with dieing HDD's and Knoppix but I have never had this issue. I burned a CD using the latest ISO and Ubuntu seen both the main HDD and my external. I just copied all the contents of the main HDD over to the external. All went well and I could browse and view all the files from the external HDD after the transfer using the live CD. Unfortunately I am having an issue seeing the external HDD in Windows. As soon as I hook the drive up - windows says I need to Format it(Which I won't do obviously). But if I boot the live CD I can still see and use the files. How do can I get windows to see the drive and files without destroying data? I have done Tons of searching but am getting nowhere. I would really appreciate the help.


-Dan


Please copy this into your terminal from the live cd. Then show us the output. We need to see the information of your external HD. 
 
```
sudo fdisk -l
```

---

### Post by SecretCode on 2010-12-01
> **julio_cortez said:**
> Let's start with a stupid question: is it NTFS or FAT/FAT32? I guess so (otherwise it's normal that Windows doesn't see it), but better be sure about that.

And if it's NTFS, did you format it like that from the Live CD? That can be unreliable (in my experience) - best to format to ntfs from a windows machine.

---

### Post by Vaphell on 2010-12-01
+1 to jahid suggestion
use live cd to do the reverse operation - mount windows made ntfs partition of the computer and dump stuff from the external drive there, shutdown linux when done, reboot to windows, voila.

---

### Post by yensed on 2010-12-01
I formatted the external HDD in Windows 7 before using it - NTFS. Windows does give it a drive letter but says it needs to be formatted before use, as if it had never been used before. I am tempted to do the reverse Copy+Paste but am paranoid it will cause the windows drive to suddenly be unusable outside of the live cd like it has with the external drive. I will paste that info into the terminal and be back.

---

### Post by yensed on 2010-12-01
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf196081

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       77826   624924672    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32a99f61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

The 640gb HDD is my internal drive I am using on this notebook. The external one is the 250GB drive.

---

### Post by akand074 on 2010-12-01
> **yensed said:**
> I formatted the external HDD in Windows 7 before using it - NTFS. Windows does give it a drive letter but says it needs to be formatted before use, as if it had never been used before. I am tempted to do the reverse Copy+Paste but am paranoid it will cause the windows drive to suddenly be unusable outside of the live cd like it has with the external drive. I will paste that info into the terminal and be back.

Copying data from the external drive to the Windows drive won't affect Windows at all. It's just data, has nothing to do with the OS. Unless you actually touch system files but I assume what your trying to put back is documents/pictures/videos etc. It won't be a problem. Just boot into the live cd, mount the external hard drive, mount the windows partition, and just copy and paste them to whatever folder you want.

---

### Post by yensed on 2010-12-01
> **akand074 said:**
> Copying data from the external drive to the Windows drive won't affect Windows at all. It's just data, has nothing to do with the OS. 
Thats what I figured as well when I used Ubuntu to transfer files from the internal HDD to the external. Then I ended up with an external HDD which I previously was able to use under windows suddenly only being accessible under Ubuntu. I didn't format it or change anything from inside Ubuntu to make it that way. Just a Copy from internal and a Paste to external... But I am going to give it a shot anyway. I really appreciate all the help.

---

### Post by runeh76 on 2010-12-01
> **yensed said:**
> Thats what I figured as well when I used Ubuntu to transfer files from the internal HDD to the external. Then I ended up with an external HDD which I previously was able to use under windows suddenly only being accessible under Ubuntu. I didn't format it or change anything from inside Ubuntu to make it that way. Just a Copy from internal and a Paste to external... But I am going to give it a shot anyway. I really appreciate all the help.


Pls read what i posted earlier..

---

### Post by yensed on 2010-12-02
Well Thankfully everything went smoothly when using the Ubuntu live CD to transfer content off the external HDD onto the internal Windows drive. I still don't quite understand what happen to the external drive under Ubuntu to cause Windows to not see its contents as it was showing it as NTFS and was properly formatted in windows ahead of time - but I'm glad nothing was lost. I Will find a different approach in the future should I do something like this again. But I think I have them convinced they need to keep proper backups at this point so it was a good lesson for everyone I guess.

Thanks again, All of you, for the help. Its pretty amazing the things I were able to do right off a live CD. Ubuntu is fantastic and will probably end up on a couple old notebooks I've got around here. Any idea where I can get those Ubuntu stickers that look like Windows OS stickers which come on PC's? > **runeh76 said:**
> hmm if u used linux live-cd to copy data... I think that live-cd change ur files permission or maybe better to say change ur files to Linux file system "read only in linux" and thats why windows doesnt recognize that. Try another bootable software.

By the way i didnt understand so well.. Did u went their machine and put ur hd in?
My friends parents used DVD's as a backup source though it had been a very long time since they did that anyway. With XP booting but being almost useless, I figured I could just backup everything to an external HDD. They were unable to burn discs even if they wanted and transferring large amounts of data which didn't have proper backups on a system that crashed hourly was too risky. The whole goal was to simply install a fresh copy of XP - I wasn't keeping anything or getting anything in return.

Again, Thanks for all the help everyone!

---

### Post by runeh76 on 2010-12-02
Good job!!

---

