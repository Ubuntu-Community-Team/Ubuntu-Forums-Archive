---
title: "Remove extra HD entries In Browser Places"
date: 2010-05-09
forum: General Help
---

### Post by sandman3838 on 2010-05-09
Hello
I hope someone can help, this is really annoying.

Take a look at the "screen shot attachment" you will notice that I have multiple listings for the HD - WIN_XP, WIN_7 and GAMES.  I was checking out both NTFS CONFIGURATION TOOL and MOUNTMANAGER.  I Removed MOUNTMANAGER but the multiple listings remain?

Ideally I would like to have the ability to Mount and Unmount any drive from the File Manager except ARCHIVE this drive I need to mount as Ubuntu Boots up.

Suggestions?


keivn@kj-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d586f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d7d0d7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sdb2           15201       30401   122102032+   f  W95 Ext'd (LBA)
/dev/sdb5           15201       30401   122102001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66305c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08860a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19929   160079661    7  HPFS/NTFS
keivn@kj-desktop:~$

---

### Post by lmarmisa on 2010-05-09
Type this command with all the duplicated disks unmounted:

> 
ls -l /media/
Check if there are files or directories with the names of the duplicated drives in the output of the command.

---

### Post by sandman3838 on 2010-05-09
Thanks for the quick reply...

Here is the results and everything was unmounted.

keivn@kj-desktop:~$ ls -l /media/ 
total 20
drwxr-xr-x 2 root root 4096 2010-05-09 00:08 ARCHIVE
lrwxrwxrwx 1 root root    7 2010-05-08 16:40 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-05-08 16:40 floppy0
drwxr-xr-x 2 root root 4096 2010-05-09 00:07 GAMES
drwxr-xr-x 2 root root 4096 2010-05-09 00:07 WIN_7
drwxr-xr-x 2 root root 4096 2010-05-09 00:07 WIN_XP
keivn@kj-desktop:~$

---

### Post by lmarmisa on 2010-05-09
I think that these directories are the problem. I believe that the system did not remove this directories by some reason (maybe a crash).

I recommend you to rename this directories and then check if your problem disappear:

> 
sudo mv /media/GAMES /media/RUBBISH_GAMES
sudo mv /media/WIN_7 /media/RUBBISH_WIN_7
sudo mv /media/WIN_XP /media/RUBBISH_WIN_XP
Restart your system when you finish the rename process.

If this solution fixes the problem, you could remove this rubbish directories later.

Best regards,

Luis

Edited: ONLY RENAME THE DUPLICATED DIRECTORIES!!!

---

### Post by sandman3838 on 2010-05-09
Hello

Thanks for the help.

Still an issue.

As you can see I can Mount & Unmount three of the drives.  However the lower three I can't even rename.  I do however get an error message.

See Attachments!

Perhaps I should reinstall those two program that I removed?  Just a thought?

---

### Post by lmarmisa on 2010-05-10
Another idea: try to rename (or even delete) the three directories starting the system from a Ubuntu LiveCD.

An important question: do you detect duplicated names of directories after you rename them?.

Best regards,

Luis

---

### Post by sandman3838 on 2010-05-10
Got it!
I just went a head and unplugged the extra HDs and rebooted the system.  Then I plugged them back in and booted back in again.  Now there is just one entry of each.

Thank you so very much for your help.  :P

---

