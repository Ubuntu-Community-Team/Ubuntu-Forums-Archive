---
title: "Ubuntu does not see External USB Drive"
date: 2010-09-08
forum: General Help
---

### Post by meandshadow on 2010-09-08
Hello Everyone ):P 
Back with Ubuntu after a few years absence... I have a Durabook (handbuilt laptop by Gammatech in California) wich is 2 years old and was running Vista, I had install Ubuntu and was running it along Vista but I decided that I prefer using Ubuntu a the sole system so I reloaded it using the whole hardrive (250GB) and now it won't reconized my USB external drive which holds all of my files, pictures, music & few programs ie: Windows XP, Vista & Ubuntu backups... Everything else seems to work fine including watching comercial DVD (thanks to Totem w/xine)and perhaps some screen glitches once in awhile and a slower operating system then before the reinstall. How can I get this problem fix...?
I should mentioned that not only it worked before when I had dual system installed but other devices work fine... in all USB ports.

---

### Post by NightwishFan on 2010-09-08
Reboot the machine with the device plugged in, and please post the output of:
```
sudo fdisk -l
```

---

### Post by meandshadow on 2010-09-08
> **NightwishFan said:**
> Reboot the machine with the device plugged in, and please post the output of:
```
sudo fdisk -l
```
tried the reboot & it didn't work... Still no f drive image and the result of typing sudo fdisk -1 in the terminal turned out this info...


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002664f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29654   238194688   83  Linux
/dev/sda2           29655       30402     6001665    5  Extended
/dev/sda5           29655       30402     6001664   82  Linux swap / Solaris

---

### Post by NightwishFan on 2010-09-08
It seems it is not detected. Perhaps try this:

Boot with the device unplugged, and open up the log file viewer and go to 'System Log'. Then plug the device in and post (if any) text appears in bold.

---

### Post by meandshadow on 2010-09-08
> **NightwishFan said:**
> It seems it is not detected. Perhaps try this:

Boot with the device unplugged, and open up the log file viewer and go to 'System Log'. Then plug the device in and post (if any) text appears in bold.

I just did all that and first
 after the usual log for the wireless Lan connection process there was only one line of text in bold...

Sep  8 16:50:01 michel-laptop AptDaemon: INFO: Initializing daemon

Then I booted Google Chrome to get back to this post and this is the new Hi-lighted text...

Sep  8 16:54:57 michel-laptop kernel: [  385.780596] lo: Disabled Privacy Extensions
Sep  8 16:55:01 michel-laptop kernel: [  389.858685] lo: Disabled Privacy Extensions
Sep  8 16:55:02 michel-laptop AptDaemon: INFO: Quiting due to inactivity
Sep  8 16:55:02 michel-laptop AptDaemon: INFO: Shutdown was requested

Beats me if I know what that means...

---

### Post by meandshadow on 2010-09-08
Hi everyone ! I just tried to mount the device using this code even though I wasn't seeing it..
sudo mount -t ntfs-3g /dev/sdb1 /media/external
 and here's the results if it help figure it out...
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

---

### Post by NightwishFan on 2010-09-08
If it were mountable it would have shown up with the fdisk command.

---

