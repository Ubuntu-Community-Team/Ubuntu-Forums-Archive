---
title: "was i right"
date: 2006-02-19
forum: General Help
---

### Post by sjoseph on 2006-02-19
i was under the impression that when i booted under linux, and wrote to a fat32 partition, that i would be able to access it when i booted in windows. the goal here would be to practice using linux, especially for downloading photos and music, but than have access to them in windows. right or wrong..does having a /media/windows file have anything to do w this.

---

### Post by sande on 2006-02-19
Well having a /media/windows file? I didnt exactly get u, because when u have the fat32 drive it is /media/hda5 or something like that. and if we need to write something into a fat32 drive we have to have root access.
I simply open nautilus from the terminal using sudo and voila I can write into a fat32 drive.
```
sudo nautilus
```

---

### Post by cotcot on 2006-02-19
Correct , you can access FAT as well from linux as from windows. This is the way to do : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
Yes, /media/windows has something to do do with. This is the "mount point" under linux for the FAT. You can give the mount point also other names.

A shared FAT is ok as long as you do not have individual files of more than 4 GB. You can consider a shared ext2 partition as an alternative. Ext2 is linux native and accessible from windows by simply installing the ext2 driver (see [http://www.fs-driver.org](http://www.fs-driver.org) )

---

### Post by akniss on 2006-02-19
[QUOTE=sande]Well having a /media/windows file? I didnt exactly get u, because when u have the fat32 drive it is /media/hda5 or something like that. and if we need to write something into a fat32 drive we have to have root access.
I simply open nautilus from the terminal using sudo and voila I can write into a fat32 drive.
```
sudo nautilus
```[/QUOTE]


I'm no expert on linux or permissions, but I don't think you need to be root to write to a fat32 partition.  I've never had to use sudo to access my fat32 partition.  As far as I understand, fat32 doesn't even support file ownership, so all users should have access to the fat32 drive/partition.  Someone can correct me if i'm wrong.  I only bring this up because it seems like an inherently bad idea to use 'sudo nautilus' for anything but rare circumstances.

---

