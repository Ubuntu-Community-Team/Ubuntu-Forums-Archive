---
title: "Pre-existing RAID 1+0, problems getting raid assembled"
date: 2006-01-23
forum: General Help
---

### Post by cecilkorik on 2006-01-23
Hi! I just upgraded a server from SuSE 7.2 to Ubuntu-server 5.10. I've got things mostly under control but I am having serious issues getting the RAID back up and running.

The fishy part is, it's detecting the two sub-raids, /dev/md0 and /dev/md1 (both RAID1) but it cannot assemble them into /dev/md2 (which was a RAID0 striped across the two RAID1s) Yes, I *do* have a backup, but I'd prefer not to have to use it.

Specifically, the error is that, when I try to assemble /dev/md2, it says that both /dev/md0 and /dev/md1 are "busy" and cannot be opened. I'm beginning to suspect the error might be with how the /dev/md0 and /dev/md1 are put together. (I did not put them together, they were automatically assembled somehow) I've tried stopping them using "mdadm -S /dev/md0" and I get the same error: "mdadm: fail to stop array /dev/md0: Device or resource busy"

I need a hand here. It doesn't help that I'm only familiar with raidtools, not mdadm.

Here's some diagnostic output I hope will be helpful for anyone willing to take a look:

root@behemoth:~# mdadm -Q /dev/md0
/dev/md0: 55.92GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md0: device 0 in 2 device undetected raid0 md2.  Use mdadm --examine for more detail.

root@behemoth:~# mdadm -Q /dev/md1
/dev/md1: 55.92GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md1: device 1 in 2 device undetected raid0 md2.  Use mdadm --examine for more detail.

root@behemoth:~# mdadm -Q /dev/md2
/dev/md2: is an md device which is not active
/dev/md2: is too small to be an md component.

root@behemoth:~# cat /proc/mdstat
Personalities : [raid0] [raid1] 
md1 : active raid1 hdh[1] hdf[0]
      58633280 blocks [2/2] [UU]
      
md0 : active raid1 hdg[1] hde[0]
      58633280 blocks [2/2] [UU]
      
unused devices: <none>

root@behemoth:~# mdrun /dev/md2
mdadm: cannot open device /dev/md0: Device or resource busy
mdadm: /dev/md0 has no superblock - assembly aborted
mdadm: cannot open device /dev/md0: Device or resource busy
mdadm: /dev/md0 has no superblock - assembly aborted

root@behemoth:~# mdadm -S /dev/md0
mdadm: fail to stop array /dev/md0: Device or resource busy

---

### Post by awi on 2006-01-23
Try to get some mor info with "--detail" option, from mdadm, like this:

```
# mdadm --detail /dev/md0
# mdadm --detail /dev/md1
```

Maybe you'll find this thread. helpful.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=294404](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=294404)

Are you aware of the raid10?

[http://cgi.cse.unsw.edu.au/~neilb/01093607424](http://cgi.cse.unsw.edu.au/~neilb/01093607424)

---

### Post by cecilkorik on 2006-01-23
Well, there's something severely wrong with my mdadm tools, I think, or I'm not using them correctly. I've tried in several ways to zero the superblocks on the various drives and raids and it always gives the same error:

root@behemoth:/home/cecil# mdadm --zero-superblock /dev/hdf
mdadm: Couldn't open /dev/hdf for write - not zeroing

I'm so confused.  :confused:  Everything else can access the drives. I can fdisk them (and write the new partition table to them, causing them to fail out of the raid on reboot)  which I've tested on one of the drives. I can dd both to and from them. I wrote a large block off the start of one of the drives and dd'd it right back onto the drive and both succeeded fine. It's just mdadm that can't access the drive. Why? This seems to be the root of my problem. mdadm just plain isn't doing what I tell it to do.

---

### Post by awi on 2006-01-24
See the first link I posted before, look at Projects, that guy is one of the developers/maintainer of mdadm tool, there are newer versions, maybe you could get in touch with him to help you, or perhaps the mailing list.

---

