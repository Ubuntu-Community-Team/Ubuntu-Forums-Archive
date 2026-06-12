---
title: "what does the lock symbol mean"
date: 2006-02-18
forum: General Help
---

### Post by sjoseph on 2006-02-18
i have been trying to change ownership on to of my FAT32 partitioned drives, and somehow (my doing i'm sure), now both have a 'lock' symbol on them. i try to chown and am refused. do i have to remove this lock, if so how...

---

### Post by skirkpatrick on 2006-02-18
If you're seeing the lock symbol in Nautilus, it means you don't have write permissions to those items.  Am I correct in assuming that your are using "sudo chown" and not just "chown"?  Who does it say the owner is now?

---

### Post by sjoseph on 2006-02-18
yes you are right, i am using sudo chown, it says the owner is the root.

---

### Post by sjoseph on 2006-02-18
i'm trying to trace my steps, 
i don't think the lock was there until i followed someones advice and did this (or something like it);:

sudo mkdir /media/windows
sudo fdtsb /dev/hdb5 /windows vfat iocharset=utf8,users,umask=000 0 0

---

### Post by Sutekh on 2006-02-18
Sorry guys you can't **chown** a FAT32 partition, it doesn't support linux permissions.

However you *can* **chown** the *mount* folder.
```
sudo chown <username> /dev/hdb5
```
for example **will not work**, becuase you are trying to change ownership of the FAT32 partition /dev/hdb5, which is not a linux filesystem
```
sudo chown <username> /media/windows
```
Would work becuase you are trying to change ownership of the folder /media/windows, which would be on a linux filesystem.



**In any case** what your problem sounds like is not ownership (chown) problems but permission problems, which comes under the realm of **chmod**

If you want access to the Windows partition (which is FAT32 yes?) you should change the modes of access/permissions using **chmod**.
```
sudo chmod 777 -R /media/windows
```
For example **chmod 777** would allow *full* read/write/execute permissions to /media/windows for the owner/group owner/everyone else.  This number defines the actual permissions granted to the folder.  If you planned to allow different permissions to the mount folder (hence access to the partition), sing out and we can tell you what to change.

The **-R** makes the command recursive through all the folders underneath /media/windows.



[QUOTE=sjospeh]
sudo mkdir /media/windows
sudo fdtsb /dev/hdb5 /windows vfat iocharset=utf8,users,umask=000 0 0
[/QUOTE]
That looks almost right.

The first line is what you use to create the mount folder, to which the device (the FAT32 partition) is mounted to.

The second line should look more like this (changes in bold)
```

sudo **mount** /dev/hdb5 /**media/**windows vfat iocharset=utf8,users,umask=000 0 0
```This line does the mounting of the FAT32 partition.


You can make this mounting an automatic mount by adding a similar line to /etc/fstab.  /etc/fstab is a file with all mounting points specified.  It saves you  having to use the command **mount** each time you want to mount a partition.
```
sudo cp/etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```
This will backup /etc/fstab, by copying it to /etc/fstab_backup, and then edit it.

This line will make the mounting of the FAT32 partition occur automatically
```
/dev/hda5 /media/windows vfat iocharset=utf8,users,umask=000 0 0
```
Save the file and exit then use ```
sudo mount -a
```
To remount the partitions without needing to restart.

Good Luck

---

### Post by sjoseph on 2006-02-19
thanks for your note, should i be able to change permissions (chmod) to dev/hdb5. when i try, it seems to work, but the mode remains 755. any other thoughts. the windows media file is 777, that worked out, but how can i access that file from windows, that's my goal after all of this.

---

### Post by Sutekh on 2006-02-19
[QUOTE=sjoseph]thanks for your note, should i be able to change permissions (chmod) to dev/hdb5. when i try, it seems to work, but the mode remains 755. any other thoughts. [/QUOTE]No you **can't** change the permissions of the *device*.  That's what I said at the top of my post.  FAT32 does not support linux permissions.  chmod'ding the device (/dev/hda5) will not work.  You **can** chmod the *mount folder* (/media/windows), because it is part of a linux ilesystem.  I hope that's clear.

[QUOTE=sjoseph]the windows media file is 777, that worked out, but how can i access that file from windows, that's my goal after all of this.[/QUOTE]If the partition is FAT32 it should be recognised by Windows automatically as another hard disc.

---

### Post by sjoseph on 2006-02-19
thanks for all your help.

steve

---

