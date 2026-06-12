---
title: "File System check is always skipped at boot up"
date: 2010-09-30
forum: General Help
---

### Post by sharathcshekhar on 2010-09-30
Hi,
I have recently noticed that my HDD fsck during boot up (generally done after 30 mounts) is always skipped. A file system check has never happened. I don't remember if this is the case ever since I upgraded to Lucid or was it after I tweaked some settings. 

I am a learner who keeps tweaking some minor settings, so I am not sure if I have screwed up something. 
At boot I get the following message:
```

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
init: bootchart main process (385) terminated with status 2
init: bootchart post-stop process (399) terminated with status 127
/dev/sda1: clean, 289245/1831424 files, 1732313/7323624 blocks

```
Some times I do get a message like "File system mounted 30 times with out checked, Check forced" but exits soon after. I could not observe any errors though. 
System : Lucid Lynx 386 build, AMD - 64 bit machine, Kernel 2.6.32-24

Any help is appreciated.
Thanks in advance.

---

### Post by ridgeland on 2010-10-06
I would review /etc/fstab and try # tune2fs -l /dev/sda1 (or whatever)
I think in fstab those last two numbers say 0 0 for never check or 0 1 for check per settings (shown in tune2fs).

---

### Post by sharathcshekhar on 2010-10-09
ridgeland,
Thank you very much for your reply. fstab and tune2fs looks all right to me. I have posted the output here. Please see if you can spot anything wrong with my setup:

Fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2748989c-b6aa-475d-bc00-5ea063cdbe60 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=ebe7f4c2-2d1d-47b1-ae2b-a52ba2d8659b /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e7326fe9-edc6-4376-a355-50879c050358 none            swap    sw              0       0


```
tune2fs
```

sudo tune2fs -l /dev/sda1
tune2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          2748989c-b6aa-475d-bc00-5ea063cdbe60
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1831424
Block count:              7323624
Reserved block count:     366181
Free blocks:              5197274
Free inodes:              1538677
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1022
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8176
Inode blocks per group:   511
Flex block group size:    16
Filesystem created:       Thu Jun 24 00:48:06 2010
Last mount time:          Sat Oct  9 13:03:00 2010
Last write time:          Wed Sep 22 00:00:00 2010
Mount count:              27
Maximum mount count:      27
Last checked:             Wed Sep 22 00:00:00 2010
Check interval:           15552000 (6 months)
Next check after:         Mon Mar 21 00:00:00 2011
Lifetime writes:          23 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1576178
Default directory hash:   half_md4
Directory Hash Seed:      aa145c17-2541-4dfa-a5bc-69ba7e90d905
Journal backup:           inode blocks]


```

tune2fs on /home filesystem returned error. I saw on the net that this does not work for Logical partitions. My /home is indeed logical volume.

Please help. Thanks in advance.

---

### Post by ridgeland on 2010-10-09
This is from tune2fs for my root partition (/dev/sda7):
> Mount count:              232
Maximum mount count:      -1
Last checked:             Fri Aug 27 21:50:17 2010
Check interval:           7776000 (3 months)
Next check after:         Thu Nov 25 20:50:17 2010

-1 means it never checks based on counts. I just check every three months.

I see count = 27  and max = 27 on your /dev/sda1 which means it should be checked next boot.  Also I see you have the check interval set to 6 months.

I don't know what has gone wrong.  
Does count and max both increment each boot?
You might try setting the check interval to 30 days and see if that forces the checks.  

I know tune2fs does not work for NTFS or FAT. By "Logical" do you mean what gparted calls extended?

---

### Post by sharathcshekhar on 2010-10-10
ridgeland, 
Thank you again for your response.
> 
Does count and max both increment each boot?

No mount count is reset to 1, while maximum mount count remains at 27.
Actually at boot time, on the next boot after mount count = maximum count, I observed some error message and after digging in, I found out it was logged in /var/log/boot.log. Below are the messages I got
```

fsck from util-linux-ng 2.17.2

fsck from util-linux-ng 2.17.2

init: bootchart main process (389) terminated with status 2


init: bootchart post-stop process (404) terminated with status 127


/dev/sda1 has been mounted 28 times without being checked, check forced.

/dev/sda5: clean, 48630/3662848 files, 5067484/14649264 blocks

/dev/sda1: 291147/1831424 files (0.1% non-contiguous), 1804576/7323624 blocks

init: ureadahead-other main process (852) terminated with status 4

```
I am sure, something is not right here. Can you help me, if you see anything wrong in this?
These messages are just flashed and I get the login screen almost right after. It has tried to do a fsck, but exited with some error I think.

> 
By "Logical" do you mean what gparted calls extended? 

Yes, that is what I meant.

---

