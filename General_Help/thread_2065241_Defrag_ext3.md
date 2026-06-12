---
title: "Defrag ext3?"
date: 2012-10-01
forum: General Help
---

### Post by shreepads on 2012-10-01
> **jongkind said:**
> Pyfragtools is a winner, read this thread:
[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")

Have a similar problem but not really willing to trust that tool.

Situation is that on a 2TB ext3 drive (with > 20% free) running under Lucid 10.04.4, I have a number of highly fragmented files.

Each of these files has a extent count upwards of 20,000 (as reported by filefrag).

This causes two issues
- File transfer speed is very low ~ 10MB/s as opposed to ~ 70 MB/s for my main system drive.
- File system changes, such as creating a new folder takes *significantly* longer to complete, around 6-8 secs. Note that creating a new folder on the main system drive takes less than a second

The solution I've got is to
- Rsync them (rsync -av) to an external hard drive
- Delete the root folder containing all the fragmented files using rm -rf <folder name>
- Rsync them back from the external drive

Question, when they are copied back by rsync will they once again use the originally allocated nodes/ blocks, causing them to fragment again? If so, how to avoid that...

---

### Post by Stonecold1995 on 2012-10-01
You don't need to defrag ext3, it doesn't get fragmented.

Moving all the files to a second drive and back wouldn't put them in the same place, so yes I guess that would work, but again, I don't think ext3 gets fragmented.

Or do you mean corrupt?

---

### Post by shreepads on 2012-10-02
I've heard that ext3 doesn't get fragmented before, but the evidence I see on my own drive and several posts around the web reporting fragmentation on ext3, particularly in files downloaded via torrent clients, is compelling.

When I see 
- Files with upwards of 20,000 extents (created by a torrent client) with poor read performance and other files ON THE SAME DRIVE (not created by a torrent client) with < 300 extents with good read performance 
- A simple task like creating a new empty directory taking up to 6-8 secs, which earlier ON THE SAME DRIVE used to take < 1 sec
- The drive itself is > 20% free and comes back clean on a fsck

... I think it's fair to say that performance has degraded and the cause is fragmentation.

Do you have any substantial reason to state that ext3 doesn't suffer from fragmentation?

---

### Post by dcstar on 2012-10-02
> **shreepads said:**
> I've heard that ext3 doesn't get fragmented before, but the evidence I see on my own drive and several posts around the web reporting fragmentation on ext3, particularly in files downloaded via torrent clients, is compelling.

When I see 
- Files with upwards of 20,000 extents (created by a torrent client) with poor read performance and other files ON THE SAME DRIVE (not created by a torrent client) with < 300 extents with good read performance 
- A simple task like creating a new empty directory taking up to 6-8 secs, which earlier ON THE SAME DRIVE used to take < 1 sec
- The drive itself is > 20% free and comes back clean on a fsck

... I think it's fair to say that performance has degraded and the cause is fragmentation.

Do you have any substantial reason to state that ext3 doesn't suffer from fragmentation?

"Fragmentation" will **only** affect read/write performance of a single file.

If your system takes that long to simply create a new inode for a folder entry, it is nothing to do with fragmentation. Poor performance due to fragmentation is the penalty of the disk heads having to transverse many points on the disk surface to read the data versus one contiguous list of blocks.

You may have issues with filesystem configuration not being optimised for files of many extents, or inadequate inodes or possibly bad blocks that these files are hitting. You may even look at the journal or possibly why EXT4 is now the recommended filesystem.

---

### Post by rai4shu2 on 2012-10-02
You could always give [defragfs]("http://sourceforge.net/projects/defragfs/") a shot.

---

### Post by shreepads on 2012-10-02
> **dcstar said:**
> 
You may have issues with filesystem configuration not being optimised for files of many extents, or inadequate inodes or possibly bad blocks that these files are hitting. You may even look at the journal or possibly why EXT4 is now the recommended filesystem.

That's interesting... I did run badblocks on it a while back (within e2fsck) but not recently...

I unmounted it and ran tune2fs, can you see anything wrong here? Unable to reformat to ext4, haven't got enough external disk space it back it up completely...

```
$ sudo tune2fs -l /dev/sdc1
tune2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          0322ca9f-3cd3-4843-9360-e3ceb23dc2ed
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              122101760
Block count:              488378637
Reserved block count:     24418931
Free blocks:              98437547
Free inodes:              121890903
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      907
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Fri Oct  1 19:39:31 2010
Last mount time:          Mon Oct  1 21:27:16 2012
Last write time:          Tue Oct  2 17:34:08 2012
Mount count:              17
Maximum mount count:      34
Last checked:             Mon Sep 17 09:05:55 2012
Check interval:           15552000 (6 months)
Next check after:         Sat Mar 16 09:05:55 2013
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      1a610c36-161a-4031-aa35-8647d9656fa0
Journal backup:           inode blocks

```

Running dumpe2fs caused it to hang at this point in the output

```
$ sudo dumpe2fs /dev/sdc1
dumpe2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          0322ca9f-3cd3-4843-9360-e3ceb23dc2ed
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              122101760
Block count:              488378637
Reserved block count:     24418931
Free blocks:              98437547
Free inodes:              121890903
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      907
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Fri Oct  1 19:39:31 2010
Last mount time:          Mon Oct  1 21:27:16 2012
Last write time:          Tue Oct  2 17:34:08 2012
Mount count:              17
Maximum mount count:      34
Last checked:             Mon Sep 17 09:05:55 2012
Check interval:           15552000 (6 months)
Next check after:         Sat Mar 16 09:05:55 2013
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      1a610c36-161a-4031-aa35-8647d9656fa0
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x001306ab
Journal start:            0


```

And then after a considerable amount of thought, group wise details that ran off the screen and ended at:

```
Group 14902: (Blocks 488308736-488341503)
  Block bitmap at 488308736 (+0), Inode bitmap at 488308737 (+1)
  Inode table at 488308738-488308993 (+2)
  31953 free blocks, 8191 free inodes, 0 directories
  Free blocks: 488308994-488337407, 488337965-488341503
  Free inodes: 122077186-122085376
Group 14903: (Blocks 488341504-488374271)
  Block bitmap at 488341504 (+0), Inode bitmap at 488341505 (+1)
  Inode table at 488341506-488341761 (+2)
  28414 free blocks, 8183 free inodes, 0 directories
  Free blocks: 488341762-488370175
  Free inodes: 122085386-122093568
Group 14904: (Blocks 488374272-488378636)
  Block bitmap at 488374272 (+0), Inode bitmap at 488374273 (+1)
  Inode table at 488374274-488374529 (+2)
  3 free blocks, 8191 free inodes, 0 directories
  Free blocks: 488374533-488374535
  Free inodes: 122093570-122101760


```

---

### Post by shreepads on 2012-10-02
Correction the filesystem is only 17% free (not > 20% as I thought)...

---

