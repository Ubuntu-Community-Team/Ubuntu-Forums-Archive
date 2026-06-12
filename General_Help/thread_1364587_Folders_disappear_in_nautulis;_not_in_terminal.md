---
title: "Folders disappear in nautulis; not in terminal"
date: 2009-12-26
forum: General Help
---

### Post by onedrag42 on 2009-12-26
to start, I should mention that I am running linux mint8; but given its extreme similarity to ubuntu i figured this is the proper forum for assistance. 

I got an external HDD for x-mas and started backing my stuff upto it. After it finished I went to check and make sure it all went well, and I found that I couldnt see the folders/files. So naturally I went to the terminal.

In the terminal I could view everything, and I found if i renamed the folder, it would become visible in the file browser until I refreshed the window. I can even go into the folder and everything is displayed properly until I go back, or refresh.

I am a noob to linux and I am not sure were to start. I did a ls -la command from the terminal when in the root of the external harddrive and this was the result.
```

ls: cannot access $RECYCLE.BIN: Input/output error
total 20
drwx------ 1 whersy whersy 4096 2009-12-25 23:40 .
drwxr-xr-x 6 root   root   4096 2009-12-26 00:05 ..
drwx------ 1 whersy whersy    0 2009-12-25 19:18 backup
drwx------ 1 whersy whersy 4096 2009-12-25 18:07 Downloads
drwx------ 1 whersy whersy    0 2009-12-25 17:40 hi
d????????? ? ?      ?         ?                ? $RECYCLE.BIN
drwx------ 1 whersy whersy 8192 2009-12-25 18:03 torrent

```

Then I did another ls -la from one of my partitions on my internal HDD and the results were almost identicle for the most part[atleast those first letters were, and that was what I was looking at. here is that code
```

total 117
drwx------ 1 whersy whersy  8192 2009-12-25 23:41 .
drwxr-xr-x 6 root   root    4096 2009-12-26 00:05 ..
-rwxrwxrwx 1 whersy whersy    39 2009-12-15 07:42 .directory
drwx------ 1 whersy whersy  4096 2009-12-22 00:13 .docs
drwx------ 1 whersy whersy  4096 2009-12-24 00:03 documents
drwx------ 1 whersy whersy 94208 2009-12-25 17:59 Music
drwx------ 1 whersy whersy  4096 2009-12-17 23:31 Pictures
drwx------ 1 whersy whersy     0 2009-12-25 23:43 torrent downloads
drwx------ 1 whersy whersy     0 2009-12-15 19:57 .Trash-1000

```

Any ways, I am not sure what to do from here. Any ideas?!

Thanks,

---

### Post by Vermind on 2009-12-26
The .directory file contains file and folder names that you want hidden in nautilus. The terminal does not obey this. Try to move .directory to some other name, such as dotdirectory. Then refresh in nautilus.

I recently used this functionality to hide an Ubuntu live image I put on a usb memory stick, to reduce clutter when opening it on Linux. On windows I just set the files hidden normally, since the usb memory is FAT32.

---

### Post by onedrag42 on 2009-12-26
Alright, so I looked in my .directory folder[which by the way is NOT located on the harddrive that I cannot view properly] and all i found was the following:

```

[Dolphin]
Timestamp=2009,12,15,7,42,56

```

So i renamed it to DOTdirectory, resfreshed and nothing.

Then I copied it over to the "root" of the harddrive that I couldnt view properly, and refreshed,

still nothing.

Ideas?

---

### Post by Vermind on 2009-12-26
The $RECYCLE.BIN and the input/output error tell me that you have a windows-based file system on the portable drive, and it seems that it needs a filesystem error check. Before trying other things, I recommend you run a file system check on the drive in Windows or Linux. For NTFS, Windows is recommended; the Linux NTFS tools are careful, and tell the drive that Windows should check it even after fixing it in Linux. 

To fix the errors in Linux, you can use a partition manager or a disk tool (ubuntu has drive tool in the Admin menu). Since I am unfamiliar with Mint, I will give you a working console solution.
You can do ```
fsck -a /dev/sdx1
```
where sdx1 is your drive. You can use the command ```
mount
``` to see a list of mounted drives, for example:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc ...
none ...
udev ...
/dev/sdb1 on /home type ext4 (rw)
/dev/sdc1 on /media/Work type ext2 (rw,nosuid,nodev,uhelper=devkit)

```

In this output, we are interested in things starting with /dev/sd, since those are real devices (sd = scsi/ata disk). Check the "on ..." part for your backup drive's mountpoint. Then unmount the disk in order to do the fs check. Then use the beginning of that line for the fsck command.

---

### Post by onedrag42 on 2009-12-27
I couldn't get linux to check the NTFS file system, but ran it on a windows PC and so far so good! Haven't had time to test it extenisvely, but looks good so far. Thanks for the tip!

---

