---
title: "A non-full NTFS drive shows up as full"
date: 2009-10-12
forum: General Help
---

### Post by pyost on 2009-10-12
I've had this problem for some time now on Ubuntu 9.04, and it's about time I solved it...

I have a NTFS partition mounted on */media/data* which I use to store all my files, as I will potentially need to use them in WinXP (dual boot, obviously). The partition shows up as "119.2GB Media" and reports a total capacity of "111.1 GB", but this is not the problem - I'm sure those 8GB "disappeared" for a reason.

The problem is that I can't copy/download any bigger file to this partition because it produces an error "Error writing to file: No space left on device" - and there is **8.6 GB of free space**.

I've read about reserved space, but that's for ext2/ext3... Right? The last time I had this problem I solved it by burning some of the data to several DVDs, but that is not the solution.

Any ideas why this is happening?

---

### Post by Intrepid Ibex on 2009-10-12
Though one.. have you tried a disk check?

---

### Post by pyost on 2009-10-12
No, I haven't... Which tool would you recommend?

---

### Post by Intrepid Ibex on 2009-10-12
You could go with ntfsprogs: ```
sudo apt-get install ntfsprogs && sudo fdisk -l;read -n1
``` Press any key to continue after checking out the path to your windows partition (usually /dev/sda1, mine was /dev/sda3) by looking at the 'System' label and type the command:
```
sudo ntfsfix /dev/X
``` **OBS.** ntfsprogs will probably warn you if you have, but you should **_never_** check a mounted partition (checking mounted filesystems will most likely lead to data corruption). So before running the check, **unmount** your Windows partition, e.g.: ```
sudo umount /media/data
```


You could also do this with Windows by opening command prompt and typing ```
chkdsk c: /f /r
```
Where the '/f' command automatically fixes all errors encountered and the '/r' command locates bad sectors on your hard drive and recovers readable information (everything it can).

But if Windows doesn't recommend a disk check itself during startup, there's probably issue with ubuntu. So how much does: ```
df -h
``` and Windows itself report free space?

---

### Post by pyost on 2009-10-15
Windows shows the same amount of free/occupied space as Ubuntu, but I am able to use the free space normally - so it would have to be a problem with Ubuntu.

*sudo ntfsfix /dev/sda6* output is the following:

```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda6 was processed successfully.

```

*df-l*:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              37G  9.1G   26G  27% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  308K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  152K  994M   1% /dev
tmpfs                 994M  300K  994M   1% /dev/shm
lrm                   994M  2.5M  992M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda6             112G  103G  8.6G  93% /media/data
```

And here's the output of *sudo fdisk -l*, just in case:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3170b39c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5             136        4960    38756812+  83  Linux
/dev/sda6            4961       19457   116447121    7  HPFS/NTFS
/dev/sda7               2         135     1076292   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5746a7a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4866    39086113+   7  HPFS/NTFS

```

Windows is installed on the second hard disk, which the first is for Ubuntu and data.

---

### Post by louieb on 2009-10-15
Just a though.  I have read performance starts to drop when a partition get about 80% full. Don't know how relevant that is now with bigger hard drives -  but 93% full seems  high.

Anyway  I would boot to XP and run the disk cleanup tool, defrag and chkdsk and see if that helps.

---

### Post by pyost on 2009-10-17
Now **that's** something I would *never* expect to be the solution... But it is :\ I ran **Defrag** on that partition from Windows 7, and it took some time to complete, but it helped :)

I didn't try using all the free space (8GB), but at least 1.5GB is usable, that I did try.

However, it is still strange how Windows could use that (probably heavily fragmented) space, and Ubuntu could not...

Thanks a lot :) _Consider this solved._

---

