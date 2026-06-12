---
title: "How to get full access to Windows partitions??"
date: 2006-04-27
forum: General Help
---

### Post by minhaz4u on 2006-04-27
Could someone please tell me how to gain full access to the windows partitions from Ubuntu?
I have partitioned my harddisk in to 4...Windows is installed on a NTFS partition.I can't get any access to this partition.
I have mounted 2 other partitions in FAT32 format butI have only the permission to read the files and folders ...can't delete or move any of them.

---

### Post by Jagot on 2006-04-27
[QUOTE=minhaz4u]Could someone please tell me how to gain full access to the windows partitions from Ubuntu?
I have partitioned my harddisk in to 4...Windows is installed on a NTFS partition.I can't get any access to this partition.
I have mounted 2 other partitions in FAT32 format butI have only the permission to read the files and folders ...can't delete or move any of them.[/QUOTE]

This guide should help you.

[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

You will only be able to gain read access to the NTFS partition - you will not be able to write to it.  You should be able to have full access with the FAT32 partitions.

---

### Post by Ramses de Norre on 2006-04-27
You aren't able to write to ntfs.. You can mount them read only by adding this line in /etc/fstab (do sudo gedit /etc/fstab in terminal): ```
/dev/hda2       /media/hda2  ntfs    nls=utf8,umask=0222 0       0

```
The fat can be mounted read/write with the following line: ```
/dev/hda1       /mnt/hda1  vfat iocharset=utf8,umask=0000 0 0

```
For both: set /dev/hdxx to the correct values (you can find them with sudo fdisk -l) and /media/xxx to the proper mountpoint (must be created first with sudo mkdir /media/xxx), make a seperate mount point for every drive.

---

### Post by WoodyMahan on 2006-04-27
[https://wiki.ubuntu.com/Automaticall...8mounting](https://wiki.ubuntu.com/Automaticall...8mounting) %29

Look at the section on MANUALLY mounting.  Your fstab file needs to be updated with permissions.  There is an example line in there that shows exactly how it should look.

---

### Post by minhaz4u on 2006-04-27
I went through all the replies...All of them were really helpful...
Thanks a lottttttt **[COLOR="Red"][SIZE="4"]WoodyMahan,Ramses de Norre n Jagot[/SIZE][/COLOR]** ...
My prob is solved now.... 
**[COLOR="DarkRed"][SIZE="5"]I got one more reason to b'com a happy UBUNTU USER[/SIZE] [/COLOR]**;)

---

