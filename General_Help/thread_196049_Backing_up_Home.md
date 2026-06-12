---
title: "Backing up Home"
date: 2006-06-13
forum: General Help
---

### Post by Fred Doolie on 2006-06-13
Assumption: All I really need to back up is my /home, right?

mkdir /media/usbdisk/BackupOfHome

copy  Verbose Everything /home/fred/*   /media/usbdisk/BackupOfHome/

compare /media/usbdisk/    /home/fred/

How do I do those last two lines in the proper syntax? I'm a real noobee.

Thanks

---

### Post by aysiu on 2006-06-13
KDar has differential backups.

Or were you intent on learning how to do things from the terminal?

---

### Post by Fred Doolie on 2006-06-13
[QUOTE=aysiu]KDar has differential backups.

Or were you intent on learning how to do things from the terminal?[/QUOTE]

Re:KDar
Works great. Thanks

Re:The Terminal
Yes. Might as well learn to do things right.

---

### Post by mannheim on 2006-06-13
You could simply do
```

cp -a /home/fred/. /media/usbdisk/BackupOfHome
diff -r /home/fred /media/usbdisk/BackupOfHome

```

There are more robust methods. You could use rsync as a command-line tool.

---

### Post by mlind on 2006-06-13
IMO tar archiver is very nice and easy backup tool from terminal, which can preserve
file permission and perform incremental archiving too. You can do backups over ssh
too using a pipe.

---

### Post by Fred Doolie on 2006-06-14
Thanks. After playing around a bit and seeing permission error messages fly by I changed it to:

sudo cp -a -v /home/fred/. /media/usbdisk/BackupOfHome
sudo diff -r /home/fred /media/usbdisk/BackupOfHome

Added the "sudo" and the "-v" parts

---

### Post by mannheim on 2006-06-14
Great! Of course, using a "real" archiving tool like tar or kdar (or any backup program) will have advantages. 

Just using "cp", you only ever have access to the most recently backed-up version of a file, not older ones of course. Another point is that a tar archive can record owners and permissions for files in the archive: if the usb disk is formatted as FAT32 or something, then copying files to the usb disk will lose that info.

---

### Post by Mr.Auer on 2006-06-14
This is how I do my backups, both of root and home...According to some howto somewhere..

To backup the root without unneeded folders (like /media etc):
tar cvpzf backup.tgz --exclude=/home --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=backup.tgz --exclude=backup_home.tgz --exclude=/mnt --exclude=/sys /

To backup home:
tar cvpzf backup_home.tgz  --exclude=/lost+found  --exclude=backup.tgz --exclude=backup_home.tgz /home

To restore:
tar xvpfz backup.tgz -C /

The folder to be archived is the last one, for some reason in some other distros and Hoary I think, the folder came first and switches after...This changed in Breezy I think and caused some bewilderment in me ;)
Using this method you will have to make the missing directories after unpacking the root on an empty partition, like /home, /media and so on, or it will cry upon booting that those are missing..and the permissions need to be correct.

---

