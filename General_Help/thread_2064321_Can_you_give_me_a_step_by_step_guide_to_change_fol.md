---
title: "Can you give me a step by step guide to change folder ownership from root?"
date: 2012-09-29
forum: General Help
---

### Post by Terryfab24 on 2012-09-29
I am really new to ubuntu and I'm so confused, so please excuse my ignorance.

I have two drives on my computer an 80gig and 500gb. I have ubuntu installed on the 80gb drive but have all my media on the 500gb drive. I have changed the directory setting for my music and video files to look at the 500gb harddrive instead of the original default folder on the drive that ubuntu is installed on. However, when i tried to add files to my music and video folders on the larger drive I apparently do not have permission to do that or modify the folder in anyway at all since it is owned by the root.

I have tried a couple of suggestions posted in this forum but I can't seem to find anything that works and I keep getting operation not permitted. Can someone please provide me with a step by step idiot's guide to changing my permissions? I really need some help because I am completely lost. Maybe I have even set everything up incorrectly. I am willing to remount the drive or anything that's necessary (don't worry i have everything backed up on an external drive)...I really feel that I didn't properly format the drives in the first place....

Any help will be appreciated.

---

### Post by oldfred on 2012-09-29
Welcome to the forums.

What format are partitions with your data. You can follow this, just put in your UUID.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Terryfab24 on 2012-09-29
This is what I have...my 500gb is the one with /media

/dev/sda2  vfat             /windows       F328-FCD2
/dev/sda5  swap             <swap>         506d3665-b66b-468c-8b45-0680b317ea7e
/dev/sda6  ext4             /              045cabcf-fc7c-4fd2-b1e8-030fb069e3c0
/dev/sdb1  vfat             /media         89F1-4EA8

---

### Post by CatKiller on 2012-09-29
FAT doesn't understand permissions, so you need to use fstab to control access.

 [https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32_and_FAT16_Partitions](https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32_and_FAT16_Partitions) has an example of the kind of entry you might use.

---

### Post by Terryfab24 on 2012-09-29
> **CatKiller said:**
> FAT doesn't understand permissions, so you need to use fstab to control access.

 [https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32_and_FAT16_Partitions](https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32_and_FAT16_Partitions) has an example of the kind of entry you might use.

Yeah I am really confused :confused:...I went to your link and i'm getting /mdeia/500gb a response of "File exists" when i run the command sudo mkdir /media/500gb

Can i just reformat my drive and try to remount it? I guess I'm used to the way windows looks at drives...Like if i go to my computer i'll be able to see what ever drives exist on my cpu..I'm so totally lost on managing disks on ubuntu

---

### Post by oldfred on 2012-09-29
It looks like you have already mounted it under /windows so you cannot mount it a second time.

Are you sure you want to use FAT? I did use that years ago and lost all my backups. They were compressed files over 4GB and FAT only can save files up to  4GB, no large multimedia files or anything very large. FAT also does not have a journal, so when it gets corrupted chkdsk will take longer and may not be able to recover or recover all your data. 

It you need Windows compatibility better to use NTFS. It can store large files and has a journal.

This is older and has an example of mounting a FAT partition in fstab.

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

One advantage of Linux is you do not use d: for a partition. You can give it any name you like. If you like 500gb that is fine as a mount point, but you only can have one with that name. And names are case sensitive. Once a mount point is created, you have it until you delete it even if not using it.

---

### Post by Terryfab24 on 2012-09-29
> **oldfred said:**
> It looks like you have already mounted it under /windows so you cannot mount it a second time.

Are you sure you want to use FAT? I did use that years ago and lost all my backups. They were compressed files over 4GB and FAT only can save files up to  4GB, no large multimedia files or anything very large. FAT also does not have a journal, so when it gets corrupted chkdsk will take longer and may not be able to recover or recover all your data. 

It you need Windows compatibility better to use NTFS. It can store large files and has a journal.

This is older and has an example of mounting a FAT partition in fstab.

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

One advantage of Linux is you do not use d: for a partition. You can give it any name you like. If you like 500gb that is fine as a mount point, but you only can have one with that name. And names are case sensitive. Once a mount point is created, you have it until you delete it even if not using it.

Mhhh...I guess I will just reformat my drive using NTFS...just had an issue trying to mount it before why i tried FAT but then once I did that I got all those issues with permissions and root ownership and what not...

---

### Post by oldfred on 2012-09-29
Because Windows formats neither FAT32 nor NTFS support Linux ownership and permissions, you can only set defaults when you mount the partitions.

Examples posted before show good default settting,  but you can have different ones also. I have just used "defaults" and that has worked.

---

### Post by Terryfab24 on 2012-09-29
> **oldfred said:**
> Because Windows formats neither FAT32 nor NTFS support Linux ownership and permissions, you can only set defaults when you mount the partitions.

Examples posted before show good default settting,  but you can have different ones also. I have just used "defaults" and that has worked.

Thanks for you help....I decided to just scrap it and do a complete reinstall...things are running smoothly...just have to get used to ubuntu...

---

### Post by HiImTye on 2012-09-30
looks like you gave up on mounting it to the second locations, but you could remount it to a second location using:
```
mount --bind /original/mount/folder/ /second/mount/folder/
```

---

