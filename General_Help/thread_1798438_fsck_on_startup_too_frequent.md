---
title: "fsck on startup too frequent"
date: 2011-07-06
forum: General Help
---

### Post by ceejay on 2011-07-06
Hi

Yes, I know there are already several threads on similar topics! I know that my 11.04 system should do a file system check every 30 boots, and that I can tune that number with tune2fs if I want (it's an ext2 file system).

However, my system is doing the check much more often than that - perhaps after 2, 3 or 4 boots. It's not consistent, though. It happens either with shutdown or reboot. I am using the applets in the top tool bar to shutdown or reboot - there seem to be two, both are having the same problem.

Here is a typical output of a dumpe2fs command, taken just before a reboot which triggered a file system check.

```

dumpe2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          5bf1dcc5-cbe4-420d-b93c-51516fbefbec
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      filetype sparse_super
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              2637824
Block count:              5273344
Reserved block count:     263667
Free blocks:              4212050
Free inodes:              2472686
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Last mount time:          Wed Jul  6 11:08:25 2011
Last write time:          Wed Jul  6 11:09:39 2011
Mount count:              2
Maximum mount count:      30
Last checked:             Wed Jul  6 10:53:24 2011
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128

```

You'll see a mount count of 2 and max mount count of 30.  So, why did it fsck when I rebooted seconds later?

None of the file system checks are finding errors, as far as I can see, though if there is a log I should be looking at then please point me at it!

Any ideas?

TIA

---

### Post by dargaud on 2011-07-06
Have you tried running fsck manually (after umounting of course) ?

---

### Post by seawolf167 on 2011-07-06
Two things, first, run the following command to set the frequency to say 50 boots

```
sudo tune2fs -c 50 /dev/sda1
```

where /dev/sda1 is your boot device, i.e. from 

```
sudo fdisk -l
```

then reboot, and if *fsck* starts, let it finish completely, then see if it continues to happen on subsequent boots.

---

### Post by ceejay on 2011-07-06
Thanks for the responses, though I don't think I am any further forward.

@dargaud: this is my root disk so I can't unmount it - it's the only partition live in this system. There are others on the disk but they are not in use and not referenced in /etc/fstab

@seawolf167: I'm not sure what changing the max count to 50 is going to do for me, given that it is already at 30, but I'm game for anything... so I changed the setting, rebooted, it checked the file system, I let it complete. I was then able to reboot it about 5 or 6 times - before the fsck kicked in again. And again.

Note that I am always letting the fsck complete, so I really can't see what it's complaining about!!

Any more ideas?

---

### Post by seawolf167 on 2011-07-07
> **ceejay said:**
> 
@seawolf167: I'm not sure what changing the max count to 50 is going to do for me, given that it is already at 30, but I'm game for anything... so I changed the setting, rebooted, it checked the file system, I let it complete. I was then able to reboot it about 5 or 6 times - before the fsck kicked in again. And again.

I was thinking that somehow the fsck count had be modified, and a change would push it back to where it had been. If it is continuing to happen, however, I'm not sure what else to try. Hopefully someone more experienced with this chimes in.

---

### Post by psusi on 2011-07-07
When you reboot, rather than boot from the hard drive, boot from the livecd and run dumpe2fs from there.  See if it still says the filesystem state is not clean.  If it does, then fsck is being run because for some reason, the filesystem is not being unmounted before the reboot.

By the way, why are you using ext2?  It is ancient and obsolete.  You should be using ext4.

---

