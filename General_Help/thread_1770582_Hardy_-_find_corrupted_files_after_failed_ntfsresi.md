---
title: "Hardy - find corrupted files after failed ntfsresize"
date: 2011-05-29
forum: General Help
---

### Post by jcjveraa on 2011-05-29
Hey all,

I just messed up a ntfsresize operation by unplugging the power while doing it, by kicking my power adapter with my foot...

Anyway, now that I've done that I can detect that there are several errors in the file system when I run ntfsresize again (with -f as it won't run normally because the chkdsk /f flag has been set).

Luckily the ntfs partition is a 'non essential' one mainly containing music and photo's, but of course I do really want to recover the photo's.

I was wondering: is there any way for me to find out which files might have become corrupted without Windows chkdsk? My machine is in a remote location (now: it's in my home while I've gone to my parents) so I don't have immediate access to the disk to attach it to a Windows machine.

I've searched for this, but mostly people are concerned with fixing the filesystem and not just looking to see which files might have been corrupted.

I'm using 8.04 server edition, connecting to it via Putty, and I'm pretty new to linux in general.

Thanks for any pointers!

```

user@computername:~$ sudo ntfsresize -f -s 920G /dev/sdb1
ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to set locale, using default 'C'.
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 989464621568 bytes (989465 MB)
Current device size: 989464625152 bytes (989465 MB)
New volume size    : 919999996416 bytes (920000 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Cluster accounting failed at 86721498 (0x52b43da): missing cluster in $Bitmap
Cluster accounting failed at 86721499 (0x52b43db): missing cluster in $Bitmap
Cluster accounting failed at 86721500 (0x52b43dc): missing cluster in $Bitmap
Cluster accounting failed at 86721501 (0x52b43dd): missing cluster in $Bitmap
Cluster accounting failed at 86721502 (0x52b43de): missing cluster in $Bitmap
Cluster accounting failed at 86721503 (0x52b43df): missing cluster in $Bitmap
Cluster accounting failed at 86721504 (0x52b43e0): missing cluster in $Bitmap
Cluster accounting failed at 86721505 (0x52b43e1): missing cluster in $Bitmap
Cluster accounting failed at 86721506 (0x52b43e2): missing cluster in $Bitmap
Cluster accounting failed at 86721507 (0x52b43e3): missing cluster in $Bitmap
Filesystem check failed! Totally 992114 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
```

---

### Post by jcjveraa on 2011-05-30
Didn't get anywhere with this, but I don;t require an answer any longer - thanks for your time

---

### Post by bpb_21 on 2011-06-01
This is kind of a tangent to your question, but what is the Linux/Ubuntu equivalent of Windows/DOS chkdsk?  I use Gparted but I don't think it actually scans the disk for bad sectors as chkdsk does.  I'm sure there's something out there I just don't know about, but what...?

---

### Post by jcjveraa on 2011-06-02
> **bpb_21 said:**
> This is kind of a tangent to your question, but what is the Linux/Ubuntu equivalent of Windows/DOS chkdsk?  I use Gparted but I don't think it actually scans the disk for bad sectors as chkdsk does.  I'm sure there's something out there I just don't know about, but what...?
As far as I know there is no linux chkdsk equivalent voor NTFS partitions. The best you can get is the type of error ntfsresize produces, indicating bad clusters. For other kinds of partitions you can use 'fsck', although I haven't seen a list of supported partition types for that program other than ext2 (nor did I thoroughly look for it, must be somewhere). 

I 'solved' my problem by attaching my disk to a windows box, which then automatically ran chkdsk. Didn't see any output of what it found, and neither can I find some logs, so I'm just hoping I didn't lose any data - no way to confirm.

Edit: or read this: [http://en.wikipedia.org/wiki/Badblocks](http://en.wikipedia.org/wiki/Badblocks)

---

