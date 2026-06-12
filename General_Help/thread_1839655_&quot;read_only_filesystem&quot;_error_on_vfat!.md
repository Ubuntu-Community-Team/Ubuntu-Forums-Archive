---
title: "&quot;read only filesystem&quot; error on vfat?!"
date: 2011-09-06
forum: General Help
---

### Post by gcbzzzz on 2011-09-06
seems the same issue as archive [http://ubuntuforums.org/showthread.php?t=97415](http://ubuntuforums.org/showthread.php?t=97415)

Here's how the driver is mounted. I was able to delete a several dirs, some not.

```
/dev/sdg1 on /media/70FC-635B type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```


```
inutil$ rm -fr 102_PANA/
rm: cannot remove `102_PANA/P1020990.JPG': Read-only file system
rm: cannot remove `102_PANA/P1020991.JPG': Read-only file system
rm: cannot remove `102_PANA/P1020992.JPG': Read-only file system
```

dir 101_PANA was removed without any trouble. Other images in 102_PANA were also removed fine.

It was a microSD in a SD adapter. so i unmounted, removed the microSD and mounted it directly just to try to refresh the drive table info. same error.

sudo rm also give's me the same error.

all file permissions are "-rw-r--r-- 1 1000 1000"

...i tried lsatr thinking it's the right way to show fat attributes, but i think i was mistaken since it gave me errors on every vfat file i tried.

Update: it may have been the dumb formating done by the camera..

```
$fdisk -l 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdg1               1         969     7783461    b  FAT32
Warning: Partition 1 does not end on cylinder boundary.
```

```

(0) ~
inutil$ sudo fsck /dev/sdg1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
Reclaimed 141 unused clusters (4620288 bytes).
Free cluster summary wrong (64579 vs. really 64720)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdg1: 216 files, 178224/242944 clusters

(1) ~
inutil$ sudo fsck /dev/sdg1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 2
Reclaimed 222 unused clusters (7274496 bytes).
Free cluster summary wrong (64579 vs. really 64720)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdg1: 216 files, 178224/242944 clusters

(1) ~
inutil$

```

now i could delete the files. partition is still out of boundary.

Why I couldn't delete files because of unclaimed clusters?!

---

### Post by 3rdalbum on 2011-09-06
> **gcbzzzz said:**
> 
```

(0) ~
inutil$ sudo fsck /dev/sdg1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
Reclaimed 141 unused clusters (4620288 bytes).
Free cluster summary wrong (64579 vs. really 64720)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdg1: 216 files, 178224/242944 clusters

(1) ~
inutil$ sudo fsck /dev/sdg1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 2
Reclaimed 222 unused clusters (7274496 bytes).
Free cluster summary wrong (64579 vs. really 64720)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdg1: 216 files, 178224/242944 clusters

(1) ~
inutil$

```

now i could delete the files. partition is still out of boundary.

Why I couldn't delete files because of unclaimed clusters?!

If Linux notices a filesystem problem, it immediately remounts the device as read-only, to prevent data loss and to prevent the problems from getting worse (which might result in complete filesystem failure). You can't delete files when the filesystem is read-only.

Now that you've run fsck (claims not to have touched the filesystem, but the exit code 1 says that it's corrected the problems) the problems are fixed and Linux can now mount the filesystem as read/write.

---

### Post by gcbzzzz on 2011-09-07
thanks for the explanation, still one doubt....

mount clearly says rw. And there's nothing in the syslog.

should I have been looking somewhere else or is all this silent?

---

