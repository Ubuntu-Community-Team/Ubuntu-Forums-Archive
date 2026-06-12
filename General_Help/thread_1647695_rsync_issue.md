---
title: "rsync issue"
date: 2010-12-17
forum: General Help
---

### Post by musendrophilus on 2010-12-17
Currently running Meerkat. I have a folder for my website on my computer and I'd like to have it update to my external usb hdd. So I use the following command:

$ rsync - av /home/mouse/site /media/usbhdd

which spits out:

sending incremental file list
rsync: mkdir "/home/adrian/media/SimpleDrivePS" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

I can open /media/usbhdd/ with Firefox, I can touch it and create a file on /media/usbhdd and delete the file from /media/usbhdd but I don't know if I'm not grasping a finer point which is giving me difficulty in my endeavor.

---

### Post by dcstar on 2010-12-17
> **musendrophilus said:**
> Currently running Meerkat. I have a folder for my website on my computer and I'd like to have it update to my external usb hdd. So I use the following command:

$ rsync - av /home/mouse/site /media/usbhdd

which spits out:

sending incremental file list
rsync: mkdir "/home/adrian/media/SimpleDrivePS" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

I can open /media/usbhdd/ with Firefox, I can touch it and create a file on /media/usbhdd and delete the file from /media/usbhdd but I don't know if I'm not grasping a finer point which is giving me difficulty in my endeavor.

Is the external filesystem some sort of rubbish like FAT?

---

### Post by musendrophilus on 2010-12-19
> **dcstar said:**
> Is the external filesystem some sort of rubbish like FAT?

Good question, I'm not really certain and when I checked the properties of my external HDD I didn't see anything saying "This disk uses NTFS/FAT32/whatever". Where would I look to get this info?

---

### Post by papibe on 2010-12-19
> **musendrophilus said:**
> Where would I look to get this info?

Try:
```
$ mount -l
```
or
```
$ sudo fdisk -l
```
Regards.

---

### Post by musendrophilus on 2010-12-19
Thank you! The external disk is NTFS, I'm still able to r/w the disk also I can 'touch' the disk, create a file then delete it too.
I'm uncertain why rsync would have kittens when dealing with it.

---

### Post by CharlesA on 2010-12-19
The error message looks strange.

Try running rsync like this:

```
rsync -ai /home/mouse/site /media/usbhdd/
```

---

### Post by musendrophilus on 2010-12-19
> **CharlesA said:**
> The error message looks strange.

Try running rsync like this:

```
rsync -ai /home/mouse/site /media/usbhdd/
```

Yes, that did it! Thank you!

---

### Post by dcstar on 2010-12-20
> **musendrophilus said:**
> Thank you! The external disk is **NTFS**, I'm still able to r/w the disk also I can 'touch' the disk, create a file then delete it too.
I'm uncertain why rsync would have kittens when dealing with it.

NTFS does** not** support Linux files/folders that start with "." These are illegal file names in NTFS.

You cannot correctly sync hidden files/folders (like the many ones that are in /home trees) to non-Linux filesystems.

---

