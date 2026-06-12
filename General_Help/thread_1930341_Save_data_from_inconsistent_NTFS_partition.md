---
title: "Save data from inconsistent NTFS partition"
date: 2012-02-23
forum: General Help
---

### Post by s0ulman1 on 2012-02-23
Hello everybody.

Here is the problem I've been fighting with for a few days now: my Windows XP laptop stopped booting, throwing blue screen at me with "UNMOUNTABLE_BOOT_VOLUME" error. Long story short, I found out the reason was that the NTFS partition of my HDD that Windows was installed on got corrupted somehow.

First I decided to solve Windows trouble with Windows stuff. I had no boot cd, but I managed to boot into recovery console from a usb stick. I ran **chkdsk /r**, but it stopped at 25% with no activity going on with the disk. **map** showed that the partition couldn't be recognized as NTFS. I ran **fixboot** and **fixmbr** and then the file system was recognized, but the problem remained.

I then decided to seek assistance from the allmighty Linux. I got myself a Ubuntu live usb and tried a few tricks, but nothing seemed to help.
I've tried fsck, and it gave me ```
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
``` that I wasn't able to fix even though I tried a couple solutions from google.

I've tried to mount it and to force mount it with ```
sudo ntfs-3g -o force,rw
```, but it came back with an error: ```
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error

``` saying that NTFS is inconsistent (no kidding?) and that I should run chkdsk /f (yeah, right).

I've also tried ntfsfix, but even after an optimistic message ```
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.

``` I still couldn't mount the bloody thing.

Now, I have abandoned hope to rescue the HDD, but I want at least my data back. Is there any way I save anything from that partition?

Here is our hero by the way:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf10ee396

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+   7  HPFS/NTFS/exFAT
/dev/sda2        62910540   312560639   124825050    f  W95 Ext'd (LBA)
/dev/sda5        62910603   312560639   124825018+   7  HPFS/NTFS/exFAT

```Also, is there maybe some tool I could use from a different installation of Windows that can help me with this situation?

---

### Post by oldfred on 2012-02-23
Chkdsk only fixes some things on each pass. I would try at least once more.

ntfsfix only makes minor repairs and sets chkdsk flag so window will run chkdsk on next reboot.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by s0ulman on 2012-02-24
> **oldfred said:**
> Chkdsk only fixes some things on each pass. I would try at least once more.

ntfsfix only makes minor repairs and sets chkdsk flag so window will run chkdsk on next reboot.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
I've tried to run chkdsk at least 5 times, all with the same result.

Thanks for the links.

I've run TestDisk but it didn't help me much.

But the ice has been finally broken: I've imaged the partition with GNU ddrescue and I'm currently running the recovery process from the image with Foremost. It seems to go well, but the output is a huge heap of files with names like 0865625.jpg. I don't mean to complain, but is there a way to recover my files in a more organized manner? I don't want to go through all my browser cache to find some photos. :(

---

### Post by oldfred on 2012-02-24
If it is photos or music there is internal data you can use to rename files. I had text files and many backups were recovered, so I hd to grep for data and then compare files. It can be a massive task.

I think some of the same processes work regardless of which tool you used to find the files.
Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

