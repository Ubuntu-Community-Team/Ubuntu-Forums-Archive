---
title: "Secondary HDD issue"
date: 2010-04-21
forum: General Help
---

### Post by inputpower on 2010-04-21
Hello All,

I have a Dell 620 PC tower with a 160 g HDD loaded with ubuntu server edition. I added a second HDD for media storage. I formated the drive ext3 the same as the first drive. After mounting the drive I did not have the ability to create folders or add items to the drive. I used GParted to format the drive to FAT32 with much successs. I was able to create folders and move data back and forth. I tested this with other HDDs and ext4 and nothing worked unless the second HDD had FAT32. I am seeking to know why this did not work. 
-thanks

---

### Post by oldfred on 2010-04-21
The default when you auto mount do not include all the permissions and ownership that specifing a mount in fstab does. For NTFS and FAT there are no resetable permissions & ownership as they do not support that within the file system.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by Sin@Sin-Sacrifice on 2010-04-21
Security. All you have to do is mount the drive and then ```
sudo chown user:group /media/drive
``` Replace drive with actual mount point.

---

### Post by john newbuntu on 2010-04-21
Oldfred's reply would have already answered your question.
But as a quick side note, think of partitioning of your new drive, get off of fat stuff and run fsck on those partitions if ext*.

---

### Post by inputpower on 2010-04-21
This is great information.  Is using FAT32 a bad idea or a good idea? It seems that FAT32 is easier since it just connects and there is  nothing more to do.  If I have a Windows partition it should be able to read the drive. If I format the drive to ext3 would I have the same flexibility? I hope my media storage future is a Drobo but until I set that up I will go with this, but better suggestions are welcome.
-Thanks for the help

---

### Post by oldfred on 2010-04-21
Three years ago I was using FAT32 as then the NTFS driver in Ubuntu was new and had a few issues. But I was copying files larger than 4GB not realizing it was not capable of that. I now have converted any shared with windows to NTFS and only use FAT on USB keys where they are small anyway. But I use windows so little now that most of my data is in ext3 data partitions.

---

