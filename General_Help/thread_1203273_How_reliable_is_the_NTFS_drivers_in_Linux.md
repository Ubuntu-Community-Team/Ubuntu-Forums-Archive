---
title: "How reliable is the NTFS drivers in Linux?"
date: 2009-07-03
forum: General Help
---

### Post by g003y on 2009-07-03
I'm running Ubuntu 9.04 on an AMD64 machine and I have several Windows formatted partitions (NTFS) on it. [br] In the past I have been warned to not write to NTFS volumes in Linux since the NTFS driver isn't fully implemented and may corrupt the file system.[br]  That was several years ago so I wonder what is the status of this today. Has it been around long enough so that I can completely rely on the drivers and write, delete, modify files and defragment NTFS volumes?[br] Are there any caveats to be aware of as of today regarding this?

---

### Post by Legace on 2009-07-03
The ntfs-3g driver Jaunty uses is very reliable. I've been using it for a long time on several computers, and never have I faced any issues using it :)

---

### Post by AnonCat on 2009-07-03
I regularly transfer files between the two filesystems and have never encountered a problem.

---

### Post by prshah on 2009-07-03
> **g003y said:**
> I can completely rely on the drivers and write, delete, modify files and defragment NTFS volumes?[br] Are there any caveats to be aware of as of today regarding this?

As others, even I have had no problems with NTFS read, write, edit, copy, move, resize, delete, etc etc. I've copied files large and small, with various filenames and quite possibly all combinations. I've copied back and forth files with Korean, Chinese or Japanese characters without any problems (though the actual characters themselves are unreadable). I've also backed up and restored NTFS partitions with partimage without problems (though for some reason, after restoration, a diskcheck is triggered with Windows starts)

So I'd suggest it's safe enough.

As an additional note: You cannot defragment a drive through linux, be it vfat or ntfs.

Also you cannot use any "chkdsk" utilities on the ntfs partitions. As far as I know, fsck.ntfs (or equivalent 3rd party utilities) are not yet ready. So if you run into a problem with your ntfs partition, you will have to rely on Windows chkdsk.

---

### Post by WitchCraft on 2009-07-03
It works, has never caused any damage to my Windows partition, and I used and am using it often.

You will have a problem mounting an NTFS usb stick if he hasn't been properly unmounted.

The solution:
```

sudo mount -t ntfs-3g /dev/sdxy /mnt/usbdrive [COLOR="Red"]-o force[/COLOR]

```

The only thing is that you might have problems if the NTFS stick is corrupted.

If you can't mount it anymore, or copying/deleting a file from/to a USB stick with plenty of free memory is impossible, then (if it's not a permission isssue) it is due to a corrupt USB stick.

On Windows, you then run chkdsk /r, which most likely repares any damage.

I don't know if fsck -t ntfs-3g /dev/sdxy exists, but it might do the same, just in case.

---

### Post by g003y on 2009-07-03
Thank you for your replies, It's good to know that the drivers are reliable although they are not as forgiving as Windows "legacy" drivers when it comes to corrupted NTFS volumes.
 
I have run into the problem with non-mountable USB sticks after removing one without unmounting it first. It was quite inconvienient since no Windows computer was around. I managed to make it mountable again after chkdsk-ing it in Windows, but still some files were unreadable (as if they were corrupted) in Linux and OsX although they were perfectly fine in Windows (It was actually FAT32 formatted).
 
I guess that this may also apply to NTFS formatted harddrives if one encounters for example a power surge.

---

### Post by prshah on 2009-07-03
> **g003y said:**
> not as forgiving as Windows "legacy" drivers when it comes to corrupted NTFS volumes.
 
I have run into the problem with non-mountable USB sticks after removing one without unmounting it first ... (It was actually FAT32 formatted).
 

I'd use the word "proprietary" rather than "legacy".

And FAT32 (vfat) partitions / drives can be easily corrected with fsck (.vfat). Actually, the command fsck is just a front for the actual for the specific filesystem; for ext3 systems, the command automatically invokes fsck.ext3, for fst, fsck.vfat, etc.

---

### Post by WitchCraft on 2009-07-03
> **g003y said:**
> Thank you for your replies, It's good to know that the drivers are reliable although they are not as forgiving as Windows "legacy" drivers when it comes to corrupted NTFS volumes.
 
I have run into the problem with non-mountable USB sticks after removing one without unmounting it first. It was quite inconvienient since no Windows computer was around. I managed to make it mountable again after chkdsk-ing it in Windows, but still some files were unreadable (as if they were corrupted) in Linux and OsX although they were perfectly fine in Windows (It was actually FAT32 formatted).
 
I guess that this may also apply to NTFS formatted harddrives if one encounters for example a power surge.
 
Exactly, but if it has not been unmounted, it is normally not corrupted. It's just a protocol in the filesystem, and if that states that it hasn't been unmounted, you can't automount it in linux. 
 
As said, in this case use: mount -t ntfs-3g /dev/sdxy /mnt/folder -o force
 
(the -o force tells linux to fix the protocol and mount, obviously, windows does this automagically)
and it will mount to /mnt/folder
 
(except if you did not create this folder)
you can create it using: mkdir -p /mnt/foldername

---

