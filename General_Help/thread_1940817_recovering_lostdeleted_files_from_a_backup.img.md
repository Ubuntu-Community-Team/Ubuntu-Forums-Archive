---
title: "recovering lost/deleted files from a backup.img"
date: 2012-03-14
forum: General Help
---

### Post by ibod on 2012-03-14
Hi all


Is it possible to recover lost/deleted files from within a backup.img file. while that .img file is mounted using the loop device ?

To be clear the files were lost/deleted prior to the creation of the backup and the original hard drive is no longer available.

---

### Post by 2F4U on 2012-03-14
It may be possible, depending on how exact the image is. This articles will give you a starting point on how to do it:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.webupd8.org/2009/03/recover-deleted-files-in-ubuntu-debian.html](http://www.webupd8.org/2009/03/recover-deleted-files-in-ubuntu-debian.html)
[http://ubuntumanual.org/posts/357/recover-your-deleted-files-in-ubuntu](http://ubuntumanual.org/posts/357/recover-your-deleted-files-in-ubuntu)

---

### Post by Helen McCall on 2012-03-18
If you deleted the files before backup, then the backup will not have copies of them. If the original disk is no longer avaialable, then it is unlikely  you can recover them.

---

### Post by 2F4U on 2012-03-18
> **Helen McCall said:**
> If you deleted the files before backup, then the backup will not have copies of them. If the original disk is no longer avaialable, then it is unlikely  you can recover them.

Ever heard about recovering deleted files? Files are not really gone just because you delete them, unless you use secure delete options. If the backup software creates an exact copy of the disk, it will also include the deleted stuff.

---

### Post by varunendra on 2012-03-19
> **2F4U said:**
> ....[COLOR=Red]**If**[/COLOR] the backup software creates an exact copy of the disk....
^^this is the key.
Unless it is a byte-by-byte image of the disk, it won't have the data that although 'physically' existed on the disk, but was logically deleted.

So it really depends upon 'how' the image was created, using what software and method. Any file backup tool would obviously backup only the data that logically exists on the disk. Even disk imaging tools, unless explicitly instructed, would only image the 'logically existing' data area in order to keep the image size small.

However, if the image is created with any data recovery software like testdisk, or with a disk imaging software while explicitly opting to do a block-by-block or sector-by-sector imaging of the disk, then it would certainly hold all the data that physically existed during backup (even if was logically deleted), and hence any data recovery tool like testdisk/photorec can recover the data from it.

---

### Post by ibod on 2012-03-21
Hi all 

Sorry for the time taken in getting back on this, I have been away on work. 

Just for information, sorry I guess I left this out of the first post

The img Files were created using a ubuntu 11.10 live CD as below

I made one img file of the whole hard drive 
and 
I made another img file of the XP installation in its logical drive in its extended partition 


```

sudo dd if=/dev/sda of=/media/clone/sdaclone.img

sudo dd if=/dev/sda5 of=/media/clone/sda5clone.img

```

Thanks  2F4U I will work through this and let you know the result

---

