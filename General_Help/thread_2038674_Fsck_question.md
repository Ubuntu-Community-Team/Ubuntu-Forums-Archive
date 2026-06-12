---
title: "Fsck question"
date: 2012-08-07
forum: General Help
---

### Post by Jungleboss on 2012-08-07
When I run a read-only fsck on my root filesystem I get errors:

```
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 4456450 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 4456451 was part of the orphaned inode list.  IGNORED.
Inode 4456452 was part of the orphaned inode list.  IGNORED.
Inode 4456453 was part of the orphaned inode list.  IGNORED.
Inode 4456454 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (18294656, counted=18294353).
Fix? no

Inode bitmap differences:  -(4456450--4456454)
Fix? no

Free inodes count wrong (4781350, counted=4781340).
Fix? no


/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 109274/4890624 files (0.2% non-contiguous), 1242752/19537408 blocks
```

But I've rebooted the server and forced filecheck of root:
[IMG]http://s9.postimage.org/5j7i3l6tp/fsck1.jpg[/IMG]

But read-only fsck still reports errors after reboot. My question. Can the read-only filecheck be trusted?

If you look at the image of the boot fsck of the root filesystem there's no text of it being 'clean'. Does this mean it's not?

---

### Post by mcduck on 2012-08-07
No, it's not clean, based on the output every time fsck asked you if it should fix the errors or not you told it to not fix them... ;)

---

### Post by Jungleboss on 2012-08-07
> **mcduck said:**
> No, it's not clean, based on the output every time fsck asked you if it should fix the errors or not you told it to not fix them... ;)

Thanks for the interest in my problem :)

But you misunderstood me. The text in code tags are the read-only fsck when OS is booted and root FS is mounted.

The image is from when fsck is run during boot.

---

### Post by mcduck on 2012-08-07
> **Jungleboss said:**
> Thanks for the interest in my problem :)

But you misunderstood me. The text in code tags are the read-only fsck when OS is booted and root FS is mounted.

The image is from when fsck is run during boot.

I don't see any image in your post.

Anyway, if the automatic fsck during boot really doesn't give you opportiunity to answer "yes" and do the actual fixes, then try booting into recovery mode and running fsck there, or alternatively booting with a live-USB/CD and running fsck on that partition there.

---

### Post by Jungleboss on 2012-08-07
> **mcduck said:**
> I don't see any image in your post.

Anyway, if the automatic fsck during boot really doesn't give you opportiunity to answer "yes" and do the actual fixes, then try booting into recovery mode and running fsck there, or alternatively booting with a live-USB/CD and running fsck on that partition there.

You see no image under the text "But I've rebooted the server and forced filecheck of root:" ?

Anyway the URL to it is:
[http://s9.postimage.org/5j7i3l6tp/fsck1.jpg](http://s9.postimage.org/5j7i3l6tp/fsck1.jpg)

Ok, I'll try recovery mode.

---

### Post by Jungleboss on 2012-08-07
I ran a recovery cd and checked root for errors. None found and FS is clean according to fsck.

But after rebooting into Ubuntu server read-only fsck still says "filesystem still has errors"

I guess the read-only check can't be trusted?

---

### Post by mcduck on 2012-08-07
> **Jungleboss said:**
> I ran a recovery cd and checked root for errors. None found and FS is clean according to fsck.

But after rebooting into Ubuntu server read-only fsck still says "filesystem still has errors"

I guess the read-only check can't be trusted?

just to make sure, did you check *root* or */dev/sda1*? (the root when running a live-CD would of course be the root of the live-CD)

The fsck that happens at boot time definitely should be reliable, even for the root partition.

---

### Post by Jungleboss on 2012-08-07
> **mcduck said:**
> just to make sure, did you check *root* or */dev/sda1*? (the root when running a live-CD would of course be the root of the live-CD)

The fsck that happens at boot time definitely should be reliable, even for the root partition.

Sorry for being sloppy in my description.

After booting the live cd I ran: fsck -fv /dev/sda1 (my boot partition)

No errors and clean FS.

But after rebooting into Ubuntu server again and running, on the mounted root FS, fsck -nv /dev/sda1, fsck still says "filesystem still has errors".(-n executes fsck read-only)
It seems that fsck with the read-only parameter -n can't be trusted? Can anyone confirm.

---

