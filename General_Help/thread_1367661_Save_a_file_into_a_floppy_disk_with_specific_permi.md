---
title: "Save a file into a floppy disk with specific permission"
date: 2009-12-29
forum: General Help
---

### Post by chang5562 on 2009-12-29
It may sound strange, who in this day still uses the floppy disk.  Don't blame me.  I am just following the manager's order.

I tried to save file (ex. in .txt format) from my program, written in python, into a floppy disk either an internal drive or an USB floppy drive.  When I did some tests and noticed that there were created with different permission tag.

When I saved (or f.write(..) by python) into the internal floppy disk, the permission carried as rwxr-xr-x, while the permission were as rwx------ when saved to the USB floppy disk.  Both actions were conducted under the user environment.

Furthermore, I noticed that when I wrote the file into the user Desktop, the file only carried the -rw-r--r-- permission.

Why there were such difference even by writing to the same floppy disk at different device.  Which ubuntu program controls the permission tag?  I believed that python is using the ubuntu underline application to save the file.

How can I save or write the file with specific permission?

---

### Post by falconindy on 2009-12-29
I'm going to assume that your floppy is formatted as vfat or ntfs. These are Windows filesystems which won't understand the concept of Linux permissions.

---

### Post by chang5562 on 2009-12-30
Yes you are right.  The original intention of the program is to process the simple text file (.txt) created by the Windows or the Linux platform, exchangable on both platforms.

If it is the filesystem formated by the Windows that can not be understood by Linux, I am puzzled with why the same saving action on Linux of different devices of the linux produced a different permission of the file?

---

### Post by Morbius1 on 2009-12-30
> How can I save or write the file with specific permission?

You can't. vfat permissions on a linux system are determined by the mount command or by instructions given by /etc/fstab or by the way linux automounts usb devices. 

I don't know about usb floppy drives but it appears that it follows the same rules as all other external usb mass storage devices. They will be automounted with with you as the owner and with read /write/execute permissions to you only. Same thing will happen if you insert a usb flash drive.

It shouldn't affect the way windows sees it though.

---

