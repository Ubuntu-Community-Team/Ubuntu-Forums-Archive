---
title: "btrfs compression problem"
date: 2011-02-16
forum: General Help
---

### Post by sanosuke001 on 2011-02-16
Hello,

I recently set up a new btrfs raid 0 on three 3TB drives in my file server. Previously, I was using six 1TB drives not raided and using NTFS after an upgrade from a windows box to ubuntu.

So anyway, btrfs raid, started working okay and then I noticed it slowed down considerably. Instead of ~30sec to unrar a file over the network (gigabit) to ~5min for the same file. Also, after a couple power outages it failed to remount upon startup. I actually had to run btrfsck to fix it.

This is my fstab entry for the fs:

```
UUID=ac313f43-8ead-4d61-95ff-e615ec2f3afb  /media/internalRAID  btrfs	compress	0  0
```

So compression is on and the UUID is for one of the three drives I have in the raid. I have no idea why it will sometimes start out seeming to work fine and then slow down excessively. 

Is there some kind of maintenance I should do on the fs? Defragment or rebuild the btree? I thought about disabling the compression (I have mostly video files; out of the 6TB I have, I think it's only compressed down 11GB) but I'm not sure if removing the compress flag from the fstab entry will create issues for any files that are currently compressed. Is there a way to have the fs re-write all the compressed files as uncompressed? 

Any help would be appreciated. I looked on the btrfs wiki but they don't have much of a help section. Thanks!

---

