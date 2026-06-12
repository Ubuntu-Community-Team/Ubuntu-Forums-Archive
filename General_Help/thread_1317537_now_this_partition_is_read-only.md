---
title: "now this partition is read-only"
date: 2009-11-06
forum: General Help
---

### Post by ray field on 2009-11-06
For a month I've been using some of my old let's call them Windows partitions under Jaunty with an old DOS application, and everything was working great until today, when suddenly I became unable to write to them. Saving from the application produced the "file not found" message typically associated with read-only permissions on the file.  Every attempt to chmod a directory stamps results in "Read-only file system"

Now, I didn't use FSTAB to set up the disk; instead, I created a mount point in Nautilus (I think) and then used symlinks from some of its directories to point at the dosemu drives.  It always worked out fine, except I had to mount the partition from the Nautilus menu at the start of every session by selecting the correct size-labeld icon. I had tried using FSTAB but I never found a satisfactory statement, and was content to open up Nautilus at the beginning of every session.

This happened since I used Partimage for backup the other night -- so, maybe this is related: I booted to a new thumbrive installation to run Partimage, but I found that even though I had not booted from the hard drive, Partimage would not allow me to back up my root partition -- so then I mounted it and unmounted it, and then I was able to run Partimage on it. That's not the partition I'm having trouble with, but is it possible maybe I changed ownerships?  I don't know how to clear this up...

---

### Post by pastalavista on 2009-11-06
Install pysdm (storage device manager). It's the easiest way to set fstab the way you want it.

---

### Post by ray field on 2009-11-06
> **pastalavista said:**
> Install pysdm (storage device manager). It's the easiest way to set fstab the way you want it.

okay, have done so, and now the partition mounts successfully at bootup.  however, everything is still read-only -- if I gksudo Nautilus, the partition comes up locked, and I can't change permissions.

the FSTAB entry looks like this:

/dev/sda5                                  /media/dosdisk_  hpfs         users,user,owner            0  0 

some kind of ownership issue?

---

### Post by michy99 on 2009-11-06
What is the output of```
ls -l /media/dosdisk_
```

---

### Post by ray field on 2009-11-06
> **michy99 said:**
> What is the output of```
ls -l /media/dosdisk_
```

basically it gives the directory listing:


total 182050
drwxrwxrwx  3 root root        6144 1999-10-07 21:30 00
-rwxrwxrwx  1 root root      200816 2003-09-23 04:57 1014s003.zip
-rwxrwxrwx  1 root root        1159 1995-01-05 15:35 1-5A.LOG
-rwxrwxrwx  1 root root        3029 1995-01-05 15:33 1-5B.LOG
-rwxrwxrwx  1 root root        2435 1995-01-05 12:05 1-5C.LOG
-rwxrwxrwx  1 root root        3041 1996-02-28 06:36 1x.des
drwxrwxrwx  2 root root        2048 2008-02-17 08:45 2008-02-17-A
drwxrwxrwx  2 root root        2048 2008-02-17 08:48 2008-02-17-B_after_adding_partz
-rwxrwxrwx  1 root root        1609 2003-08-26 07:57 6-03.CSV
-rwxrwxrwx  1 root root        2314 2003-08-26 07:55 7-03.CSV
drwxrwxrwx  2 root root        2048 1999-10-07 21:31 94-09-11.FAX
-rwxrwxrwx  1 root root         294 1996-10-24 15:38 95-11-14.BAT
-rwxrwxrwx  1 root root         325 1995-10-21 17:20 95-11-14.SYS
-rwxrwxrwx  1 root root           9 1999-11-24 17:14 acchpfs.cmd
-rwxrwxrwx  1 root root           0 2004-10-12 21:12 adaim
-rwxrwxrwx  1 root root         151 2004-12-19 06:29 addcd_for_eCS_install

etc

---

### Post by michy99 on 2009-11-06
My mistake, should have included a d```
ls -ld /media/dosdisk_
```

---

### Post by pastalavista on 2009-11-06
If all that drive is used for is data storage, you may want to change the owner to you instead of root.```
sudo chown username /media/sda5
``` or you can change it with 'gksu nautilus' by right-clicking the folder, select 'properties' and click the 'permissions' tab.

If you're dual booting Windows, you might need to boot into Windows and make sure it isn't locked for updates or that some program has kept it from shutting down cleanly.

---

### Post by ray field on 2009-11-06
> **michy99 said:**
> My mistake, should have included a d```
ls -ld /media/dosdisk_
```

drwxr-xr-x 120 root root 20480 2009-08-24 13:41 /media/dosdisk_

thanks

---

### Post by michy99 on 2009-11-06
I think you need to change the ownership to yourself. Replace USERNAME with your actual username.```
sudo chown USERNAME /media/dosdisk_
```

Reboot and see if it works now.

---

### Post by ray field on 2009-11-06
> **michy99 said:**
> I think you need to change the ownership to yourself. Replace USERNAME with your actual username.```
sudo chown USERNAME /media/dosdisk_
```

Reboot and see if it works now.

comes up:

chown: changing ownership of `/media/dosdisk_': Read-only file system

something to do with uid? did I somehow change that if I mounted it under the thumbdrive or CD?

---

### Post by michy99 on 2009-11-06
What do you get for```
sudo fdisk -l
```

---

### Post by ray field on 2009-11-06
> **michy99 said:**
> What do you get for```
sudo fdisk -l
```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4982

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1        8001    a  OS/2 Boot Manager
/dev/sda2               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5   *           2         256     2048256    7  HPFS/NTFS
/dev/sda6   *         257         320      514048+   7  HPFS/NTFS
/dev/sda7   *         321         384      514048+   7  HPFS/NTFS
/dev/sda8   *         385         639     2048256    7  HPFS/NTFS
/dev/sda9   *         640         767     1028128+   6  FAT16
/dev/sda10  *         768         895     1028128+   7  HPFS/NTFS
/dev/sda11  *         896        1150     2048256    7  HPFS/NTFS
/dev/sda12  *        1151        1405     2048256    7  HPFS/NTFS
/dev/sda13  *        1406        1533     1028128+   7  HPFS/NTFS
/dev/sda14  *        1534        2043     4096543+   7  HPFS/NTFS
/dev/sda15  *        2044        5868    30724281    7  HPFS/NTFS
/dev/sda16  *        8416        9563     9221278+  82  Linux swap / Solaris
/dev/sda17  *        9564        9691     1028128+  83  Linux
/dev/sda18  *        9692       48053   308142733+  83  Linux
/dev/sda19  *       48054       60801   102398278+  83  Linux

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009541a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         460     3694918+  83  Linux
/dev/sdb2             461         489      232942+   5  Extended
/dev/sdb5             461         489      232911   82  Linux swap / Solaris

Disk /dev/sdc: 125 MB, 125173760 bytes
8 heads, 32 sectors/track, 955 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         955      122224    6  FAT16

---

### Post by michy99 on 2009-11-06
Unmount the disk.```
sudo umount /media/dosdisk_
```Open fstab for editing.```
gksudo gedit /etc/fstab
```Replace the line for /dev/sda5 with this one:```
/dev/sda5 /media/dosdisk_ ntfs-3g utf8,umask=007,uid=1000,gid=46 0 0
```Save and exit. See if you can change the ownership now.```
sudo chown USERNAME /media/dosdisk_
```Now mount and see if it works.```
sudo mount -a
```

---

### Post by michy99 on 2009-11-06
I have to log-off for the night soon, but I will check this thread tomorrow and see how it is going. Hopefully you will have it fixed by then.

---

### Post by ray field on 2009-11-06
I can change ownership with that changed entry in FSTAB, however, it's an HPFS partition (it's an old OS/2 partition), which may be why when I try to mount it, I get:

```
NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

If I change the entry to 

```
/dev/sda5                                    /media/dosdisk_  hpfs   utf8,umask=007,uid=1000,gid=46 0 0
```

mounting gives

```
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

but my kludgey mount of that hpfs partition worked just fine.

---

### Post by ray field on 2009-11-06
right now it mounts just fine with this FSTAB entry:
```

/dev/sda5                                    /media/dosdisk_  hpfs   umask=007,uid=1000,gid=46 0 0
```

but every attempt to chown results in 

```
chown: changing ownership of `/media/dosdisk_': Read-only file system
```

---

### Post by pastalavista on 2009-11-06
> **ray field said:**
> right now it mounts just fine with this FSTAB entry:
```

/dev/sda5                                    /media/dosdisk_  hpfs   umask=007,uid=1000,gid=46 0 0
```

but every attempt to chown results in 

```
chown: changing ownership of `/media/dosdisk_': Read-only file system
```

Try
```
sudo chmod +rw /media/dosdisk_
```

---

### Post by ray field on 2009-11-07
likewise
```

chmod: changing permissions of `/media/dosdisk_': Read-only file system
```

---

### Post by ray field on 2009-11-07
oops, my bad -- set read-only because of disk errors, probably because I had pulled the plug at some point yesterday.  booted to OS/2, ran chkdsk, shut down & rebooted Ubuntu & now dosdisk_'s ownership has successfully changed.  thanks for the help.

---

