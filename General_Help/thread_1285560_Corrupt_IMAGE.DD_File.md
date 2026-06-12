---
title: "Corrupt IMAGE.DD File"
date: 2009-10-07
forum: General Help
---

### Post by riddings on 2009-10-07
I am completely lost...

Earlier today, I unintentionally deleted a hard drive partition on one of my hard drives.  Using TestDisk I attempted to restore this partition.  Although it appeared UNSUCCESSFUL in completely restoring it, it did 1)  FIND the Deleted Partition and 2) Allowed me to create a backup image with the exact  size of the partition (the partition was the same size as the active files within it).

So, now I have this 176 GB image.dd file I'm UNABLE to restore.  When I try to restore it to the formatted drive (ext4) it removes the file system and once again becomes unreadable, basically duplicating the image and I stored (which, I suppose is exactly what an image is supposed to be).

So, I wonder...  1)  Does this image file truly contain my missing work (files) that I so reckless lost and 2) Is there any hope in restoring this IMAGE.DD onto a hard drive with a filesystem so I can retrieve the files I SO DESPERATELY NEED.

Any help would be greatly appreciated, I've been working on since endlessly since yesterday...

Thanks
Richard I.

---

### Post by jbrown96 on 2009-10-07
You can try to mount the image, then you can see what was recovered. 
1) create a directory to mount it
```
mkdir Desktop/recovery
```
2) mount it ```
sudo mount /path/to/IMAGE.DD Desktop/recovery -ro
``` This will mount the drive read-only, so it won't be messed up any further. The problem is if the filesystem was damaged, then it may not even be able to mount. This is probably your best. If you can get it to mount, then you re-create the damaged partition and copy everything from the image to the new partition.

---

### Post by riddings on 2009-10-08
> **jbrown96 said:**
> You can try to mount the image, then you can see what was recovered. 
1) create a directory to mount it
```
mkdir Desktop/recovery
```2) mount it ```
sudo mount /path/to/IMAGE.DD Desktop/recovery -ro
``` This will mount the drive read-only, so it won't be messed up any further. The problem is if the filesystem was damaged, then it may not even be able to mount. This is probably your best. If you can get it to mount, then you re-create the damaged partition and copy everything from the image to the new partition.

Alright.

1)  Created the directory in Desktop

2)  Tried to mount
[INDENT]2a)  Tried. ```
 sudo mount /media/Array/image.dd Desktop/recovery -ro
``` ---  Doing this returned the MOUNT OPTIONS List

2b)  Tried. ```
 sudo mount /media/Array/image.dd Desktop/recovery
``` ---  Doing this returned, "mount: /media/Array/image.dd is not a block device (maybe try `-o loop'?)"

2c)  Tied.  sudo mount /dev/mapper/nvidia_dbafhebe1/image.dd Desktop/recovery[/CODE] --- Doing this returned, "mount: special device /dev/mapper/nvidia_dbafhebe1/image.dd does not exist
       (a path prefix is not a directory)"

[/INDENT]What am I doing wrong?

Thank you for your help,
Richard I.

---

### Post by dandnsmith on 2009-10-08
'maybe try `-o loop'?

It has given you the clue - do 
sudo mount -o loop ....

---

### Post by riddings on 2009-10-08
> **dandnsmith said:**
> 'maybe try `-o loop'?

It has given you the clue - do 
sudo mount -o loop ....

Okay.

Tried.
```
sudo mount -o loop /media/Array/image.dd Desktop/recovery
```Returned.  "mount: you must specify the filesystem type"

So, I typed in...

```
 sudo mount -o loop ext4 /media/Array/image.dd Desktop/recovery
```This returned:[INDENT]mount: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so

[/INDENT]I also tried ext3, no difference.

Examined the log...

[ 7498.376756] EXT4-fs (loop0): VFS: Can't find ext4 filesystem
[ 7519.799133] VFS: Can't find ext3 filesystem on dev loop0.


Any thoughts?

Thanks,
Richard I.

---

### Post by falconindy on 2009-10-08
The proper syntax is "-t loop". the -o flag is for specifying further options like ro, rw, etc. So, in full:

```
sudo mount -t loop /media/Array/image.dd Desktop/recovery
```

---

### Post by alphaniner on 2009-10-08
It is **-o loop**, not **-t loop**.  The filesystem type uses the -t flag, such as **-t ext4**.

That said, I think you may be SOL, unless you can find some recovery software that works with ext4.

---

### Post by riddings on 2009-10-08
> **falconindy said:**
> The proper syntax is "-t loop". the -o flag is for specifying further options like ro, rw, etc. So, in full:

```
sudo mount -t loop /media/Array/image.dd Desktop/recovery
```

I am feeling pretty ignorant at the moment...

```
sudo mount -t loop /media/Array/image.dd Desktop/recovery
```

Returns:  "mount: unknown filesystem type 'loop'"

Tried:

```
sudo mount -t ext4 /media/Array/image.dd Desktop/recovery
```

Returns:  "mount: /media/Array/image.dd is not a block device (maybe try `-o loop'?)"

Tired:
```
sudo mount -o loop -t ext4 /media/Array/image.dd Desktop/recovery
```

Returns:
"mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Oh Boy.
~Richard I.

---

### Post by alphaniner on 2009-10-08
It may be possible to run fsck on an image, maybe you could look into that.

---

### Post by riddings on 2009-10-08
> **alphaniner said:**
> It may be possible to run fsck on an image, maybe you could look into that.

Okay...  Trying it now...  I'll update everyone when it's finished...

Thanks,
Richard Iddings

---

### Post by riddings on 2009-10-08
> **riddings said:**
> Okay...  Trying it now...  I'll update everyone when it's finished...

Thanks,
Richard Iddings


Thank You.  Thank You.  Thank You. Thank You.

fsck found several discrepencies...  and FIXED them...

ran

```
sudo mount -o loop -t ext4 /media/Array/image.dd Desktop/recovery
```

And, right now, I'm looking at ALL my important files...

Thanks for all the help people!
~Richard I.

---

### Post by alphaniner on 2009-10-08
I'm actually kind of surprised that worked.  Did you run fsck on the image or the partition?  If the image, could you post the command you used?

---

### Post by riddings on 2009-10-08
> **alphaniner said:**
> I'm actually kind of surprised that worked.  Did you run fsck on the image or the partition?  If the image, could you post the command you used?

I ran fsck to check the image...

```
sudo fsck /media/Array/image.dd
```

Throughout the check it would ask me if I wanted to fix something, I'd answer yes...  It discovered hundreds of discrepencies and although I'm still copying data out of the mounted file, everything appears to be there...

Although the original filesystem on the drive where I deleted the partition was EXT4, I would have assumed testdisk when created this backup image in an attempt to restore the partition would have salvaged part of that file system, FSCK identified it as a corrupted EXT2 and asked if I wanted it repaired...  At that point, I had nothing to really lose since I felt I was at the end of my rope, I type, "Y" and away it went...

A few times it asked if I wanted to fix certain things, I'd always answer Y, and for quite awhile the terminal screen appeared pretty MATRIX like, with digits filling the terminal box scrolling forever...  

Again,
Thanks for the suggestion, it saved the day!
~Richard I.

---

### Post by alphaniner on 2009-10-08
> **riddings said:**
> I ran fsck to check the image...

```
sudo fsck /media/Array/image.dd
```

Weird, I tried to run fsck on an image I created it didn't work.  Anyway, thanks for the info.  Glad you got it worked out.

---

### Post by nicolasdiogo on 2010-01-31
FANTASTIC!!

many thanks,

i never considered running ```
fsck.ext4
``` against an image created with dd

your suggestions have saved a lot of my time and i have also learnt something good.

even when linux seems to go bad, it also has the tools for fixing the problem..

here is what i did.

created image with dd:

```
dd if=/dev/sda2 of=/media/disk/myHomeImage.dd bs=512MB

```

run fsck against image:
```

fsck.ext4 -y /media/disk/myHomeImage.dd
```

mounted image as to check that everything is fine:

```
mount -o loop -t ext4 /media/disk/myHomeImage.dd ~/Desktop/myHomeRecovered
```

and then browsed my files.


many thanks,

Nicolas

meta: ext4, corrupt, recover, filesystem, howto

---

