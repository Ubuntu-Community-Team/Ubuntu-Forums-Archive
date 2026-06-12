---
title: "reset force check default"
date: 2010-06-13
forum: General Help
---

### Post by Denny Johnson on 2010-06-13
When I ran 8.04, force check would be run every 23 boots.
The ESCAPE key allowed me to skip it that boot and it would again start force check at the next boot.

In 10.04, it gave me an option to use the C key to cancel, but it does not attempt force check at subsequent boots. It does not seem to do an automatic check any more.

How can I restore the original 10.04 setting?
Or better yet, get it to perform as it did in 8.04

Thanks

---

### Post by quixote on 2010-06-16
I'm not sure what to say about it not catching up on its filesystem checks after an abort.  It should.

To set the interval, first boot from a livecd (because it's important for the partition in question to be **unmounted** when you do this). Open a terminal (Applications>Accessories>Terminal).  Find out the designation for your ubuntu partition (unless you already know it, of course).  For instance, type ```
sudo fdisk -l    *["l" as in list]*
``` The size of the partition is usually the easiest way to tell, and it'll be an ext4 or ext3 filesystem.  Let's say it's /dev/sda1.  Then the command to set the interval is:```
sudo tune2fs -c 23 /dev/sda1
```Substitute whatever number of mounts you want for the interval, and substitute the right partition designation for your setup.

---

### Post by Denny Johnson on 2010-06-16
Thanks Quixote...........I'm too much of a novice to follow thru w/o a bit more help.
The results of the 1st command in liveCD are shown in the 1st screenshot.
I could not tell for sure which partition I should be dealing with.
I suspect it's sda7, but am not confident enuf.
I think I can rule out dev/sda6 as the grub menu indicates that as another version of 10.04 that I have installed, the result of a less than satisfying upgrade attempt.
Curious about sda3, sda5, and sda8.

The results of the same command run in the problematic, installed from CD, version of 10.04 are shown in the 2nd screenshot.

From livecd, is this what I should run?
```
sudo tune2fs -c 23 /dev/sda7
``` 

Thanks

---

### Post by jerome1232 on 2010-06-16
Just fyi there is no problem with running tune2fs on a mounted partition. So you can do it from within your installation just fine.

if you type from within your real installation it will tell you what partitions are mounted where. Should give you an idea of what your dealing with.
```
mount
```

---

### Post by Denny Johnson on 2010-06-16
Thanks Jerome..........does this mean that /dev/sda7 is the partition that I am operating on and that running the code in my previous post would be appropriate?
Thanks

---

### Post by jerome1232 on 2010-06-16
Yes /dev/sda7 is your root partition. :)

---

### Post by Denny Johnson on 2010-06-16
Thanks guys.......looks like that worked.........guess I'll find out in 23 boots

---

### Post by jerome1232 on 2010-06-16
if you use tune2fs -l /dev/sda7 it will tell you what the paramaters are all set to.

ie

```
sudo tune2fs -l /dev/direbane/data
[sudo] password for jeremy: 
tune2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          8df6ef2f-b729-4e7f-af5c-9ac475fc9d6b
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6553600
Block count:              26214400
Reserved block count:     0
Free blocks:              10535152
Free inodes:              6547470
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Thu Feb 12 21:07:34 2009
Last mount time:          Wed Jun 16 16:28:49 2010
Last write time:          Wed Jun 16 16:28:49 2010
[COLOR="Blue"]Mount count:              22
Maximum mount count:      32[/COLOR]
Last checked:             Wed Jun  2 09:12:39 2010
Check interval:           15552000 (6 months)
Next check after:         Mon Nov 29 08:12:39 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      b31cd76a-6e11-478b-8d5f-b2ea477d3174
Journal backup:           inode blocks
```

---

### Post by Denny Johnson on 2010-06-16
cool...............thanks

---

### Post by quixote on 2010-06-16
Jerome, just so I know for myself in the future: how did you determine that /dev/sda7 is the root partition?  I would have said /dev/sda3 since it's both a Linux partition and bootable.  Puzzled.  

Interesting about tune2fs being okay to run on a mounted partition.  In the early days I managed to hose a drive by running fdisk on a mounted partition, which made me permanently paranoid about mounted drives and so I got my wires crossed.

---

### Post by Denny Johnson on 2010-06-17
Hi Quixote.......not Jerome here, but /dev/sda7 was shown after the "mount" command, see attachment post #5. 
/dev/sda3 was very small, tho I still wonder what it and /dev/sda5 and /dev/sda8 are.

Based on your first post, just to be on the safe side, when I did finally run ```
sudo tune2fs -c 23 /dev/sda7
``` I did it fm CD.
Thanks

---

### Post by dcstar on 2010-06-17
> **quixote said:**
> 
........
Then the command to set the interval is:```
sudo tune2fs -c 23 /dev/sda1
```Substitute whatever number of mounts you want for the interval, and substitute the right partition designation for your setup.

There is no need to always use a mount "count", that is just the default usage when an EXT filesystem is created.

You can set the check to every N days/week/months, look at the tune2fs man page for details.

---

### Post by quixote on 2010-06-17
Hmm.  I'm still not sure I get it.  Doesn't running the "mount" command without options just default to listing whatever is currently mounted?  In other words, it's saying there's a root partition on sda7, but it's not saying you're booting from it. ?? Or am I missing something?

---

### Post by jerome1232 on 2010-06-17
Yes mount lists current mounted partitions, if he's in his installation and /dev/sda7 is listed as mounted at /, it's the only partition that would be getting fsck'd during the boot process. Thus it's the partition we need to run tune2fs on.

---

### Post by Denny Johnson on 2010-06-17
An admitted novice here....but as I understand it.............running MOUNT told me in which partition the OS, that I was operating from and wanted to tune, was located.
That's what I needed to know to run your suggested code,

---

### Post by quixote on 2010-06-20
Jerome, thanks for clarifying.  /dev/sda7 being root an all, that makes sense  #-o.  I'm still puzzled about the listing of all drives though.  sda3 is a linux drive and bootable.  But it's not /.  Weird.  I'll have to read up on what the output of fdisk -l actually means :D.

---

