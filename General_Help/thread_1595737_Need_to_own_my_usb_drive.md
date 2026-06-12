---
title: "Need to own my usb drive"
date: 2010-10-13
forum: General Help
---

### Post by fibrebiz on 2010-10-13
This is a sony walkman I'm referring to. It is mine, I am an administrator but I can't seem to change permissions.

It says the owner is root and the files are access only, I'd like to change permissions to allow create and delete file access for all users but I've been having trouble doing so.

using sudo nautillus, I've been unable to change the owner of the drive, I get the following error message:
**The owner could not be changed.**
Sorry, could not change the owner of "usb2": Error setting owner: Operation not permitted

Any suggestions?

(Using Ubuntu 10.10, if that makes a difference)

---

### Post by TeoBigusGeekus on 2010-10-13
Mount the drive and give
```
sudo fdisk -l
```
(L) in a terminal to find the mount point of the drive - let's say /media/disk.
Type
```
sudo chown yourusername /media/disk
```
Post us the results.

---

### Post by fibrebiz on 2010-10-13
Just noticed that the terminal was filled with these messages:

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Anyways, the important part of fdisk -l:

```
Disk /dev/sdc: 3902 MB, 3902799872 bytes
159 heads, 40 sectors/track, 299 cylinders
Units = cylinders of 6360 * 2048 = 13025280 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         300     3811306    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(118, 158, 40) logical=(299, 100, 24)
Partition 1 does not start on physical sector boundary.
```Next:
```
james@james-desktop:~$ sudo chown james /media/usb2
chown: changing ownership of `/media/usb2': Operation not permitted

```

---

### Post by TeoBigusGeekus on 2010-10-13
Make it
```
sudo chown james /dev/sdc1
```

---

### Post by fibrebiz on 2010-10-13
Now it says:

```
chown: cannot access `/dev/sdc1': No such file or directory
```

---

### Post by TeoBigusGeekus on 2010-10-13
Strange one...
```
sudo chown james /media/usb2
```
should do the trick.
Anyone else?

---

### Post by TeoBigusGeekus on 2010-10-13
[This]("http://ubuntuforums.org/showthread.php?t=447173") perhaps?

---

### Post by fibrebiz on 2010-10-13
I don't really understand that thread.

However, I have even more to report:
Having not done anything, ubuntu stops recognising my walkman after a certain time period, the only clue that it is plugged in is the icon in /media/usb2 and the following:

When selecting home folder (from the Places menu) with the walkman plugged in, Rythmbox starts up, and seems to recognize my walkman (named:Awesome) as a device. I can (somehow) delete files from within Rythmbox. This was confirmed when I took the MP3 player out and turned it on, to check.

Apparently, I still don't have permission to create and delete files - each folder has a lock symbol on it, and the permissions tab says root is the owner. 

```
sudo chown james /media/usb2
```still doesn't work.

This is rather confusing.

---

### Post by fibrebiz on 2010-10-13
I think I've found a workaround:

When inserting the USB, I get two new folders on the my computer space of the file browser: SONY WALKMAN and usb2.  SONY WALKMAN gives error: unable to find mount point (or something similar) and usb2 is stuck in read-only mode

Then I do these commands:

```
james@james-desktop:~$ sudo umount /dev/sdc1
james@james-desktop:~$ sudo chown james /dev/sdc1
james@james-desktop:~$ sudo mount /dev/sdc1
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab

```The usb2 folder is gone from the my computer view and the SONY WALKMAN folder operates as I wanted it to, read-write access and all.
The usb2 folder still has the read-only-must-be-root problem.

Is there a way to make this process a little easier?

EDIT: Problem solved - I used sudo nautilus and changed the permissions of usb2 successfully.
EDIT2: No it isn't. When I remove then reinsert the mp3 player, everything is undone.

---

