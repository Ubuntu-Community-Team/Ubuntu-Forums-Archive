---
title: "Issues with 2TB NTFS USB drive in Ubuntu 9.10"
date: 2010-04-20
forum: General Help
---

### Post by pbr6891 on 2010-04-20
I am running into a problem that I can't figure out with a 2TB NTFS partitioned USB attached drive under Ubuntu 9.10 ...

Drive was originally formatted on a windows XP machine and moved to the Ubuntu PC ... (this is a USB attached drive)
I started copying lots of files to the 2TB drive with Ubuntu and everything worked nicely until I hit 87% full ( 233.1Gb free, 1629.9Gb in use, 1863Gb total) (FWIW I have just short of 86000 files of various sizes on the drive) 

Then it looks like writing new files just stops ... There is no error message saying I ran out of space/directory entries/inodes/.... there is no message explaining anything ... the file system activity progress bar shows up but show no progress and there is no activity on the drive at all ...

I can read the files already on the drive, ntfsinfo ntfsfix show no problems , dmesg | tail show nothing either ...
I have tried rebooting ... and even powering everything (including the external USB drive) down ....

I can delete files and then put some back on ..still up to that limit of 87% ....

Does anyone know what's happening ? I know there is a 2TB NTFS limit but don't believe I am crossing it with a 2TB drive ... are there any other limits ?

Any suggestions would be greatly appreciated ....

---

### Post by cjhabs on 2010-04-20
Do "df -i" to see if you have any inodes free.

---

### Post by pbr6891 on 2010-04-20
> **cjhabs said:**
> Do "df -i" to see if you have any inodes free.

Thanks for the tip ....

it looks like i have plenty of free inodes
Filesystem Inodes   IUsed   IFree   IUse%   Mounted on
/dev/sdg1 244513824 90594 244423230  1%   /media/DISK-NTFS-1

---

### Post by cjhabs on 2010-04-21
> **pbr6891 said:**
> Thanks for the tip ....

it looks like i have plenty of free inodes
Filesystem Inodes   IUsed   IFree   IUse%   Mounted on
/dev/sdg1 244513824 90594 244423230  1%   /media/DISK-NTFS-1

Try running "tune2fs -l /dev/your_partition" and see what the "reserved block count" is? Typically it is 5% - maybe yours is different for some reason?

---

### Post by pbr6891 on 2010-04-21
> **cjhabs said:**
> Try running "tune2fs -l /dev/your_partition" and see what the "reserved block count" is? Typically it is 5% - maybe yours is different for some reason?

Will do ... 
FWIW last night I put the drive back onto an XP machine ... and I have no problem whatsoever adding more files on the disc from XP .. (I checked a few of the files to make sure they were transferred correctly and they were ... ) Next step it to put the drive back on the Ubuntu machine and see if I can read all the files (Ubuntu written up to where it stopped and XP written afterwards)

---

### Post by srs5694 on 2010-04-21
> **cjhabs said:**
> Try running "tune2fs -l /dev/your_partition" and see what the "reserved block count" is? Typically it is 5% - maybe yours is different for some reason?

***DO NOT DO THIS!!!!*** Pbr6891 specified that this is an *NTFS* drive, but tune2fs is a utility for ext2fs/ext3fs/ext4fs!! Chances are tune2fs will see that it's operating on an NTFS partition and will therefore do nothing but print an error message, but it's best to be safe with this and not use an inappropriate utility.

I have two diagnostic suggestions:


[list]
[*]After the copy fails, try manually copying files with unique names to the drive. If the copy fails, that suggests that the drive is running out of inodes, filename slots, or something similar, despite what the "df" output suggests. If the copy succeeds, the problem is likely a localized issue of some sort -- maybe one directory can't take more files, or maybe there's a filename issue (a filename that's legal on the source filesystem but not in NTFS).
[*]After the copy fails, unmount the drive, access it in Windows, and try copying more files to it. The same logic applies, except that this test may turn up Windows/Linux differences. You could also try running CHKDSK on the disk in Windows; maybe it'll tell you something interesting.
[/list]


More broadly, why are you using NTFS for this? Do you want to access the files in Windows? If so, you could try FAT instead of NTFS. FAT could be unsuitable, but it's also conceivable it would work better. If you don't need to access the files in Windows, then it's probably best to convert it to use a Linux-specific filesystem, such as ext3fs, ext4fs, ReiserFS, JFS, or XFS.

If you need to access the files in Windows and neither NTFS nor FAT works, you could try ext2fs or ext3fs along with the appropriate Windows driver. (I don't have a URL handy, I'm afraid.) Alternatively, you could copy the files into a tarball, as in:

```

cd /source/dir
tar cvf /dest/dir/tarball.tar ./

```

This copies the contents of /source/dir into a tarball called tarball.tar in /dest/dir (which should be wherever you've mounted the drive). You could do something similar with other archive formats, such as a zip file. I don't recall offhand if Windows understands tarballs, but I'm pretty sure it's got built-in zip support.

---

### Post by pbr6891 on 2010-04-21
> **srs5694 said:**
> ***DO NOT DO THIS!!!!*** Pbr6891 specified that this is an *NTFS* drive, but tune2fs is a utility for ext2fs/ext3fs/ext4fs!! Chances are tune2fs will see that it's operating on an NTFS partition and will therefore do nothing but print an error message, but it's best to be safe with this and not use an inappropriate utility.


Thanks for the warning ...

> 
I have two diagnostic suggestions:


[list]
[*]After the copy fails, try manually copying files with unique names to the drive. If the copy fails, that suggests that the drive is running out of inodes, filename slots, or something similar, despite what the "df" output suggests. If the copy succeeds, the problem is likely a localized issue of some sort -- maybe one directory can't take more files, or maybe there's a filename issue (a filename that's legal on the source filesystem but not in NTFS).
[*]After the copy fails, unmount the drive, access it in Windows, and try copying more files to it. The same logic applies, except that this test may turn up Windows/Linux differences. You could also try running CHKDSK on the disk in Windows; maybe it'll tell you something interesting.
[/list]


The weird thing first is that the copy actually does not "fail" ... the files stop being transferred and there is no disk activity but I don't get a popup window that say something failed and the copy aborted ... Actually the way I noticed the issue is that the progress bar in the file operation window stopped moving and was showing a time left to completion way beyond what I was expecting and constantly creeping up ...

I have tried your suggestions ... the manual file copy does not work any better ... however if I connect (USB) the drive to a Windows machine everything works like it should .. drive not full and I can still copy files on the drive ...

So I guess it looks like some weird Ubuntu / Windows difference .. (or is it a bug ?: the weird part is that it's completely silent , no warnings, no errors, no crash, dmesg shows nothing so I am not sure how to document this :confused: )

> 
More broadly, why are you using NTFS for this? Do you want to access the files in Windows? If so, you could try FAT instead of NTFS. FAT could be unsuitable, but it's also conceivable it would work better. If you don't need to access the files in Windows, then it's probably best to convert it to use a Linux-specific filesystem, such as ext3fs, ext4fs, ReiserFS, JFS, or XFS.

If you need to access the files in Windows and neither NTFS nor FAT works, you could try ext2fs or ext3fs along with the appropriate Windows driver. (I don't have a URL handy, I'm afraid.) Alternatively, you could copy the files into a tarball, as in:

```

cd /source/dir
tar cvf /dest/dir/tarball.tar ./

```

This copies the contents of /source/dir into a tarball called tarball.tar in /dest/dir (which should be wherever you've mounted the drive). You could do something similar with other archive formats, such as a zip file. I don't recall offhand if Windows understands tarballs, but I'm pretty sure it's got built-in zip support.

My main interest in using NTFS is that I can move my drives between Linux and Windows machines seamlessly ... I have some pretty large files >4GB and long file names so I am not sure that FAT would work .. 
I wasnt aware that ext3/ext3 drivers existed for windows but that might be something to look at if I can't get NTFS to work right on ubuntu !

---

### Post by srs5694 on 2010-04-21
> **pbr6891 said:**
> I have tried your suggestions ... the manual file copy does not work any better ... however if I connect (USB) the drive to a Windows machine everything works like it should .. drive not full and I can still copy files on the drive ...

So I guess it looks like some weird Ubuntu / Windows difference .. (or is it a bug ?

This sounds like a bug in the NTFS-3g driver used by Ubuntu, then. You could try contacting the NTFS-3g developers, or file a bug report with the Ubuntu developers.

It's also conceivable that the drive has a bad sector and that the NTFS-3g drivers are trying to write data to the bad sector but the Windows NTFS driver is using a different sector at this point. You'd need to use a low-level diagnostic tool to test this hypothesis.

> My main interest in using NTFS is that I can move my drives between Linux and Windows machines seamlessly ... I have some pretty large files >4GB and long file names so I am not sure that FAT would work .. 
I wasnt aware that ext3/ext3 drivers existed for windows but that might be something to look at if I can't get NTFS to work right on ubuntu !

Your best bet may be ext3fs with the appropriate drivers in Windows, then. I'm afraid I don't have much experience with those drivers, so I can't offer much in the way of help beyond pointing out that the drivers do exist. I don't know how reliable they are.

---

### Post by cjhabs on 2010-04-21
> **pbr6891 said:**
> Thanks for the warning ...


Sorry about that - I missed that.

BTW - it won't damage your drive, it can't run as it doesn't find the superblock info it needs.

Sorry again.

---

### Post by 2hot6ft2 on 2010-04-21
Just for reference and in case anyone is interested this may be of use.

Ext2fs Home Page (On March 14, 2010, version 1.41.11 of e2fsprogs was announced.)
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

Important info. about using Ext2fs on ext3 partitions here (scroll up the page to the contents for more info. about the program):
**Does the Ext2 driver access Ext3 volumes, too?**
[http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)

---

### Post by egalvan on 2010-04-21
> **2hot6ft2 said:**
> Just for reference and in case anyone is interested this may be of use.

Ext2fs Home Page 
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

Ext2 Installable File System For Windows  fs-driver
[http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)

Not clear from the original post, but these are two different drivers.

The second one does not support large inodes, which means one has to do manual formatting (the default setting is large inodes).
I used it for quite some time under XP ( and donated to the authors )..
it works well, but has not been updated yet for the inode issue.
On a large inode drive, XP shows it as un-formatted.

---

### Post by 2hot6ft2 on 2010-04-21
> **egalvan said:**
> Not clear from the original post, but these are two different drivers.

The second one does not support large inodes, which means one has to do manual formatting (the default setting is large inodes).
I used it for quite some time under XP ( and donated to the authors )..
it works well, but has not been updated yet for the inode issue.
On a large inode drive, XP shows it as un-formatted.
That explains why it looked similar but not the same as the first one.
I figured it was worth linking to for the warning information.
So does that warning NOT apply to the first program?

---

