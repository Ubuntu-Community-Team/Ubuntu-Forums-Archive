---
title: "Copying problem in Ubuntu"
date: 2010-09-18
forum: General Help
---

### Post by binoysankar on 2010-09-18
Guys i need help. the problem is that when i try to copy two files with the name(say ajax.js and Ajax.js) to a pen drive/USB it shows the options for either Replace/Skip. with the above two options either one of the ajax.js files will be copied, but i need these two files. I have also used different USB's, but no difference...

Thanks in advance.

---

### Post by lmarmisa on 2010-09-18
I believe that your problem is related to the limitations of the old FAT file system that is case-insensitive. Check if your pendrive uses this FAT format.

Maybe NTFS could solve your problem.

---

### Post by binoysankar on 2010-09-18
> **lmarmisa said:**
> I believe that your problem is related to the limitations of the old FAT file system that is case-insensitive. Check if your pendrive uses this FAT format.

Maybe VFAT or FAT32 could solve your problem.

When i try to format the USB it shows four options

1) Compatible with all systems (FAT)
2) Compatible with Linux (ext2)
3) Compatible with Linux (ext4)
4) Encrypted, compatible with Linux (FAT)

i used the first option to format but the problem still exists...

---

### Post by lmarmisa on 2010-09-18
Try to format your pendrive with the NTFS file system using Gparted.

Open a terminal and type this command to install Gparted and the ntfs packages:

```

sudo aptitude install gparted ntfsprogs ntfs-3g

```Then open System -> Administration -> GParted, select your pendrive device (be careful and do not select a hard drive), delete the FAT partition and create the new NTFS partition.

---

### Post by binoysankar on 2010-09-18
> **lmarmisa said:**
> Try to format your pendrive with the NTFS file system using Gparted.

Open a terminal and type this command to install Gparted and the ntfs packages:

```

sudo aptitude install gparted ntfsprogs ntfs-3g

```Then open System -> Administration -> GParted, select your pendrive device (be careful and do not select a hard drive), **delete the FAT partition and create the new NTFS partition.**

When i selected the pendrive i can't find the any option to delete/format(these options are disabled), the Delete icon(and others icons on the top window of Gparted) are disabled by default.

---

### Post by lmarmisa on 2010-09-18
> **binoysankar said:**
> When i selected the pendrive i can't find the any option to delete/format(these options are disabled), the Delete icon(and others icons on the top window of Gparted) are disabled by default.

I attach some captures with the steps to follow (sorry, my Ubuntu is in Spanish):


[LIST=1]
[*]Select the FAT partition and click on the delete icon.
[*]Apply.
[*]Create a new partition.
[*]Select file system ntfs and define a label (optional).
[*]Apply.
[*]The new ntfs partition is available.
[/LIST]

---

### Post by binoysankar on 2010-09-18
Ya i understood the above steps, the problem is that when i select the USB drive no icons are enabled.

Attaching the thumbnail

---

### Post by lmarmisa on 2010-09-18
You must umount your pendrive. Otherwise it is locked.

---

### Post by binoysankar on 2010-09-18
i tried unmount and after that when i double clicked the drive it shows like this...

---

### Post by lmarmisa on 2010-09-18
Close Gparted, then click the right button on the CHOMES icon of the wallpaper and select umount the device. Open Gparted again after the pendrive is umounted.

---

### Post by coffeecat on 2010-09-18
> **binoysankar said:**
> i tried unmount and after that when i double clicked the drive it shows like this...

Perhaps the filesystem is corrupted. If you are going to reformat it anyway this won't matter, but if it won't let you reformat sdb1, you can re-create a partition table which will effectively wipe the drive. It won't - it will merely rewrite the partition, but there won't be a sdb1 to upset Gparted.

In Gparted, go to Device > Create Partition Table and create an ms-dos partition table. The whole drive will now show as unformatted. Now simply create your NTFS partition in the whole space. Have you installed ntfsprogs? You need that to be able to make a NTFS partition although I think ntfsprogs comes in the box with Lucid. ntfs-3g certainly does. I don't know why someone told you to install that.

---

### Post by FahadMKS on 2010-09-18
To unmount  select Places >> Computer >> File System >> Media >> select the USB mounted there >> right click and unmount and it should do the trick.

If you are still unable to do that, please do restart the computer and plugin the usb and without accessing any application try to unmount it.

---

### Post by binoysankar on 2010-09-18
Thanks @imarmisa the problem is solved now...:D
I really appreciate for the help you have given me as i am a novice in Ubuntu... Usually when this problem occurs i try renaming one of the files, copy to USB and revert the original name after copying to another machine... now i know how to tackle this...;)

Thanks again for the help cya...):P
[]("http://ubuntuforums.org/member.php?u=955260")

---

### Post by Serpher on 2010-09-18
I believe both FAT and NTFS file-systems are case sensitive. In Window's the file Ajax.jsp and ajax.jsp would be read as the exact same thing. You can do two of the following.


1) Rename the files so they would be different if the file-system is not case sensitive.

2) If you're only going from one Linux system to another with this USB, type in the following commands after backing up your USB data:

```
sudo umount /dev/sdb1
sudo mkfs -t ext4 /dev/sdb1
```

If /dev/sdb1 doesn't work try sdc1 etc etc. You might want to run the command 'ls /dev/|grep sd??' to get a better idea.

---

### Post by lmarmisa on 2010-09-18
> **binoysankar said:**
> Thanks @imarmisa the problem is solved now...:D
I really appreciate for the help you have given me as i am a novice in Ubuntu... Usually when this problem occurs i try renaming one of the files, copy to USB and revert the original name after copying to another machine... now i know how to tackle this...;)

Thanks again for the help cya...):P


Please, mark the thread as SOLVED.

---

