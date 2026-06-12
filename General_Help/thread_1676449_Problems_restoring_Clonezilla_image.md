---
title: "Problems restoring Clonezilla image"
date: 2011-01-27
forum: General Help
---

### Post by onebir on 2011-01-27
I'm trying to restore a clonezilla created partition to get some important files out, which I carelessly forgot to backup separately while I was setting up an Ubuntu dual boot.  

I followed the instructions here ([http://ubuntuforums.org/printthread.php?t=872832&pp=75](http://ubuntuforums.org/printthread.php?t=872832&pp=75)).   To cut a long story short, the restore command eventually failed & (unsurprisingly) the resulting image couldn't be mounted. I'm new to Linux/Ubuntu & hoping I haven't somehow made a mistake which will make the data irrecoverable. I've tried to include as much relevant information as I can think of below. Any suggestions would be much appreciated....

Here are the clonezilla-created files:
```
onebir@onebir-laptop:/$ ls -lh /media/320gb_external/DellCpartn-2011-01-18-12-img
total 12G
-rwxrwxrwx 1 onebir onebir    5 2011-01-18 15:05 parts
-rwxrwxrwx 2 onebir onebir 2.0G 2011-01-18 14:26 sda2.ntfs-img.aa
-rwxrwxrwx 2 onebir onebir 2.0G 2011-01-18 14:36 sda2.ntfs-img.ab
-rwxrwxrwx 2 onebir onebir 2.0G 2011-01-18 14:43 sda2.ntfs-img.ac
-rwxrwxrwx 2 onebir onebir 2.0G 2011-01-18 14:51 sda2.ntfs-img.ad
-rwxrwxrwx 2 onebir onebir 2.0G 2011-01-18 14:58 sda2.ntfs-img.ae
-rwxrwxrwx 2 onebir onebir 1.7G 2011-01-18 15:05 sda2.ntfs-img.af
-rwxrwxrwx 1 onebir onebir   36 2011-01-18 14:19 sda-chs.sf
-rwxrwxrwx 1 onebir onebir  512 2011-01-18 14:19 sda-mbr
-rwxrwxrwx 2 onebir onebir  454 2011-01-18 14:19 sda-pt.parted
-rwxrwxrwx 1 onebir onebir  259 2011-01-18 14:19 sda-pt.sf
onebir@onebir-laptop:/$ 
```I checked the file types:
```
onebir@onebir-laptop:/$ file /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.aa
/media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.aa: gzip compressed data, from Unix, last modified: Tue Jan 18 14:19:24 2011, max speed

onebir@onebir-laptop:/$ file /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.ab
/media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.ab: data
```

Since the .aa was a gzip I tried:
```
onebir@onebir-laptop:/media$ cat /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.* | gzip -d -c | sudo ntfsclone --restore-image -o /media/320gb_external/Csda2.img -
ntfsclone v2.0.0 (libntfs 10:0:0)
Ntfsclone image version: 10.0
Cluster size           : 4096 bytes
Image volume size      : 21476204544 bytes (21477 MB)
Image device size      : 21476206080 bytes
Space in use           : 18752 MB (87.3%)   
Offset to image data   : 56 (0x38) bytes
Restoring NTFS from image ...
cat: /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.ab: Input/output error
cat: /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.ac: Input/output error
cat: /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.ad: Input/output error
cat: /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.ae: Input/output error
cat: /media/320gb_external/DellCpartn-2011-01-18-12-img/sda2.ntfs-img.af: Input/output error

gzip: stdin: unexpected end of file
```

I think this took 8ish hours to complete (I left it overnight). The command reported I/O errors for the partial archives excluding the aa file (see far right of code box). I'd previously tried to open this with other software (iso master), & wonder whether this might have affected it in some way...

The mount operation failed:
```
onebir@onebir-laptop:/$ sudo mount -o loop -t ntfs media/320gb_external/Csda2.img /mnt
[sudo] password for onebir: 
Error reading $MFT: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/loop0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```I seem to be back where I started & I'm at a bit of a loss as to what to try next....

---

### Post by Mark Phelps on 2011-01-27
From what I see, it looks like you're trying to restore an NTFS partition backup made with CloneZilla, right?

I've seen those error messages myself before and was SOMETIMES able to fix the partition by running chkdsk against it -- but to do that, you have to be able to "attach" the drive to a genuine MS Windows PC and run chkdsk from there.

There is a utility ntfsfix -- but it's not a substitute for chkdsk.

BTW, when I ran into this problem on a USB stick, chkdsk was NOT able to fix it and I lost all 16GB on that stick.  Just letting you know, it may not be recoverable.

---

### Post by onebir on 2011-01-27
> From what I see, it looks like you're trying to restore an NTFS partition backup made with CloneZilla, right?

Thanks for the suggestion. I was trying to restore a backed up NTFS partition to an image file for mounting rather than a partition. I imagine I can't run chkdsk on the image. I guess I could try to restore to a partition instead, but I'm not sure I have a suitable drive.

> BTW, when I ran into this problem on a USB stick, chkdsk was NOT able to  fix it and I lost all 16GB on that stick.  Just letting you know, it  may not be recoverable. 	
I'd assumed once I'd made a backup, I had a backup. Never occurred to me I could have made a non-usable backup. :(

---

### Post by Mark Phelps on 2011-01-27
> **onebir said:**
> I'd assumed once I'd made a backup, I had a backup. Never occurred to me I could have made a non-usable backup. :(

Been there ... really!

Caused me (in the Windows world) to STOP using Ghost because the one time I relied on it to restore an OS, the program claimed the backup was unusable!

Don't know why you're using CloneZilla to backup NTFS partitions, but I have had really oustanding success using Macrium Reflect to do just that -- but that's an MS Windows app, and you need a Windows PC (or setup) to install it.  IF you have that, it's a free download and definitely worth checking out.

---

### Post by onebir on 2011-02-02
Ah well - thanks for the help Mark. Guess I'd better try to figure if the earlier backups of those files will do.

Incidentally, I reported the problem over on the clonezilla forums, and the only suggestion they had was possible hardware error. (I was using clonezilla mainly because it seemed to be the tool of choice for this sort of task. I actually found the UI slightly confusing on the critical issue of the locations of the data for backup and the image file. I guess I'd better try it out again sometime.)

---

