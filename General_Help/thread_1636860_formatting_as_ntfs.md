---
title: "formatting as ntfs"
date: 2010-12-03
forum: General Help
---

### Post by Kateeb on 2010-12-03
well about a month ago i was using windows 7 (i have two operating systems ubuntu and windows7 don't ask me anything about that cause my brother did it and i wasn't watching him) and i got some maleware and i switched over to ubuntu and formatted it as "compatible with all systems (FAT)".  I went to reinstall windows 7 to the same hard disk space as before i formatted it and it said "windows cannot be installed to this hard disk space. windows must be installed to a partition formatted as NTFS" how do i format it as NTFS with ubuntu?

---

### Post by WorMzy on 2010-12-03
You can use gparted, or, if you prefer the command line, mkfs.ntfs is the command line tool. You will need the ntfsprogs package in either case, so install that first.

```
sudo apt-get install ntfsprogs
```

Install gparted with
```
sudo apt-get install gparted
```

launch it by running (Alt+F2)
```
gksu gparted
```

---

### Post by Kateeb on 2010-12-04
would it be ok if i right clicked it and clicked format then went to disk utility and click format volume then format as ntfs.  and if so which boxes should i check take ownership of filesystem or encrypt underlying device.

---

### Post by WorMzy on 2010-12-04
Do you get those options? NTFS doesn't support Linux file permissions, so you can't take ownership of the filesystem (at least, not directly), and encrypting isn't a good idea, because I highly doubt that Windows will play friendly with an encrypted partition unless it's been encrypted by a Windows utility.

---

### Post by karthick87 on 2010-12-04
Can you say me the command line way to format a drive.

---

### Post by smo0th on 2010-12-04
smo0th@ubuntu:~$ mkfs.ntfs --help

Usage: mkntfs [options] device [number-of-sectors]

Basic options:
    -f, --fast                      Perform a quick format
    -Q, --quick                     Perform a quick format
    -L, --label STRING              Set the volume label
    -C, --enable-compression        Enable compression on the volume
    -I, --no-indexing               Disable indexing on the volume
    -n, --no-action                 Do not write to disk

Advanced options:
    -c, --cluster-size BYTES        Specify the cluster size for the volume
    -s, --sector-size BYTES         Specify the sector size for the device
    -p, --partition-start SECTOR    Specify the partition start sector
    -H, --heads NUM                 Specify the number of heads
    -S, --sectors-per-track NUM     Specify the number of sectors per track
    -z, --mft-zone-multiplier NUM   Set the MFT zone multiplier
    -T, --zero-time                 Fake the time to be 00:00 UTC, Jan 1, 1970
    -F, --force                     Force execution despite errors

Output options:
    -q, --quiet                     Quiet execution
    -v, --verbose                   Verbose execution
        --debug                     Very verbose execution

Help options:
    -V, --version                   Display version
    -l, --license                   Display licensing information
    -h, --help                      Display this help

Developers' email address: [email]linux-ntfs-dev@lists.sf.net[/email]
Linux NTFS homepage: [http://www.linux-ntfs.org](http://www.linux-ntfs.org)

---

### Post by WorMzy on 2010-12-04
Never done it by command line myself, but presumably you use a partition tool (like parted, fdisk or cfdisk) to create a raw partition first, then run mkfs.ntfs on it.

---

### Post by karthick87 on 2010-12-04
Thank you :)

---

### Post by dFlyer on 2010-12-04
> **Kateeb said:**
> well about a month ago i was using windows 7 (i have two operating systems ubuntu and windows7 don't ask me anything about that cause my brother did it and i wasn't watching him) and i got some maleware and i switched over to ubuntu and formatted it as "compatible with all systems (FAT)".  I went to reinstall windows 7 to the same hard disk space as before i formatted it and it said "windows cannot be installed to this hard disk space. windows must be installed to a partition formatted as NTFS" how do i format it as NTFS with ubuntu?

I have not used windows in so long maybe thing have changed, but if I recall correctly, windows should give you an option to format a fat partition to ntfs.

---

