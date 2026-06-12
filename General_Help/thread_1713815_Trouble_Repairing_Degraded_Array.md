---
title: "Trouble Repairing Degraded Array"
date: 2011-03-24
forum: General Help
---

### Post by Kepesk on 2011-03-24
Help!  I recently replaced a couple of hard drives in a multimedia system that I'm using, and a couple of other drives that were in a Raid1 configuration became degraded.  No matter what I do, I can't seem to get them back in working order.

Here's the details:

The drives in question are 1.5TB drives of the same make and model.  The /proc/mdstat looks like this:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : active raid1 sda1[2](S) sdb1[1]
      1465135936 blocks [2/1] [_U]

unused devices: <none>
```

So it looks like one of the drives was somehow made into a spare.  I'm having trouble getting it out of that mode and back into a properly-functioning array.  I've tried several sets of instructions for rebuilding the array (or removing and re-adding the drive to the array) found in these forums and elsewhere.  Typically, these appear to complete successfully with no errors, but the array immediately reverts back into this configuration.  What could I be doing wrong?

One note: this partition only contains media files and is not the boot partition, so we don't need to worry about that ugliness.

Thanks for any help!

---

### Post by Kepesk on 2011-03-28
More weirdness on this one.  I checked my /etc/mdadm/mdadm.conf, and I had this line:

```
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 spares=1 UUID=3352ec86:36535d76:915d10ea:9e8e72d3
```

I removed the spares=1 line and rebooted, and the array automatically rebuilt itself.  However when it was finished, it still had the drive marked as a spare.  No change.

This is baffling.

---

