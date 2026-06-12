---
title: "Frequent disk checks in Lucid"
date: 2010-05-11
forum: General Help
---

### Post by themusicalduck on 2010-05-11
Since upgrading (fresh install) to Lucid, I've been having to go through disk checks about once or twice a week on boot. I'm not sure why Lucid thinks it needs to check my disk so often.

I looked into it a bit, and found a command that was supposed to stop disk checks happening so often. ```
sudo tune2fs -i 2w `mount | awk '$3 == "/" {print $1}'`
``` is supposed to set it to 2 weeks. I used "/home" too as I have home on a separate partition and didn't want that to be checked too.

All was fine until I booted up to find another disk check today. It can sometimes take over half an hour to finish and C to cancel doesn't always work either.

I always shutdown cleanly, unless Ubuntu completely locks up, which happens maybe once every six months (although it did happen yesterday, but I have rebooted it a few times since then with no checks happening until just now).

Is there a way to just disable checks completely? I wouldn't mind running them manually every now and then, I just don't want to do it as often as Lucid does.

---

### Post by cap10Ibraim on 2010-05-11
+1 I need to disable this check disc too 
my keyboard is not active when the scan is running so 
"press C to cancel" is totally useless

---

### Post by srs5694 on 2010-05-11
On ext2/3/4 filesystems, disk checks can be triggered for a number of reasons, including absolute time, number of mounts, and bad dismount. You should find out why your system is finding it necessary to do such frequent disk checks. I'm not sure if this information is logged in /var/log/messages or some other log file, but it might be. If it is, it'll be a message that reads something like "disk check forced; 300 days since last check." (That's actually a paraphrase; I don't recall the precise wording.)

You could also check with dumpe2fs to see what your current settings are:

```

**sudo dumpe2fs -h /dev/sda2**
dumpe2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   spare2
Last mounted on:          <not available>
Filesystem UUID:          c607bd95-8edf-4eb1-aa93-12db8f0e66a2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype sparse_super
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              51584
Block count:              206312
Reserved block count:     10315
Free blocks:              140480
Free inodes:              51378
First block:              1
Block size:               1024
Fragment size:            1024
Reserved GDT blocks:      256
Blocks per group:         8192
Fragments per group:      8192
Inodes per group:         1984
Inode blocks per group:   248
Filesystem created:       Tue Jan 13 18:12:09 2009
Last mount time:          Thu Mar 25 11:53:56 2010
Last write time:          Fri May  7 19:40:24 2010
Mount count:              1
Maximum mount count:      38
Last checked:             Wed Mar 24 15:35:16 2010
Check interval:           15552000 (6 months)
Next check after:         Mon Sep 20 15:35:16 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              128
Default directory hash:   half_md4
Directory Hash Seed:      20b461a3-ea4a-4137-9caa-f327357dc7ae

```

Note the "-h" option; if you omit it, you'll get a bunch of extra information that's unimportant for your current purpose. Note in particular the "filesystem state" ("not clean" in this example since it's currently mounted), the "last mount time," the "mount count," the "maximum mount count," the "last checked" date/time, the "check interval," and the "next check after" date/time. These values collectively determine when the next check will be performed. Perhaps you can spot something funny there, such as a mount count that doesn't return to 0 after you perform a disk check (with fsck) or an incorrect "last checked" date/time entry. If so, you might be able to use tune2fs to fix the problem -- read the tune2fs man page for details on the options you'd need. I've seen at least one report of a filesystem that just couldn't be fixed in this way; something screwey was going on. I don't recall if there was an ultimate resolution.

A more extreme solution is to back up the partition, create a fresh filesystem on it, and restore it. This might be necessary if there's some subtle corruption that's preventing some field from being reset appropriately. AFAIK only the ext2/3/4 family require periodic full checks. If you want to do away with them entirely, you can use ReiserFS, JFS, or XFS instead. Of course, the mandatory periodic full checks are there for a reason (namely, to catch errors that can creep in from time to time), but you might decide to take the (fairly small) chance of missing such errors, or you might schedule manual full checks yourself.

---

### Post by fbobraga on 2010-05-12
> **cap10Ibraim said:**
> +1 I need to disable this check disc too 
my keyboard is not active when the scan is running so 
"press C to cancel" is totally useless

it also happens here: it's annoying because the check is very slow...


> **themusicalduck said:**
> Since upgrading (fresh install) to Lucid
(...)
 It can sometimes **take over half an hour to finish** and C to cancel doesn't always work either.
(...)
it makes me miss so much the karmic check (extremely fast :P), and feel that something is wrong: seems that there is **no hard-drive activity** during the "slow" (70%++) part of the test - the same behavior occurs in my laptop and desktop...

---

### Post by ignasigarcia on 2010-05-13
same here. there is no disk activity after 70%, and it takes more than 20 minutes to so that part...

---

### Post by nucleuskore on 2010-05-20
Same problem here on my wife's Acer AS5732Z-4867. This continued desspite applying all updates. We got so fed up we reinstalled 9.10 and it's fine now.

---

### Post by fbobraga on 2010-05-27
last updates seems to fixed it: quick check here, today

---

