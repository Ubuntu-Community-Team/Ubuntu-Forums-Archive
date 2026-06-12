---
title: "pulling my hair out with mdadm"
date: 2010-10-05
forum: General Help
---

### Post by spankmeister7 on 2010-10-05
It's been days that I've been with this and I'm getting to the end of my wits.

I tried to create a RAID-5 volume with three identical 1tb drives. I did so, but I couldn't mount the new volume after a reboot. Mdadm --detail told me that of the three drives, two were in use with one as a hot spare. This isn't what I wanted.

So I deleted the volume with the following commands:

mdadm --stop /dev/md0
mdadm --zero-superblock /dev/sdb /dev/sdc /dev/sdd
mdadm --remove /dev/md0

Okay.

Then I rebooted the machine, and used fdisk to delete the linux raid partitions and re-write an empty partition table on each of the drives. I rebooted again.

Now I'm trying to start over. I purged mdadm, removed the /etc/mdadm/mdadm.conf file, and now I'm back at square one.

Almost.

Now for whatever reason I can't change the partition tables on the drives (/dev/sdb /dev/sdc /dev/sdd). When I try to make a new ext3 filesystem on one of the drives, I get this error:

"/dev/sdb1 is apparently in use by the sytem; will not make a filesystem here!"

Um, what?

I think that the system still thinks that mdadm still has some weird control of my drives and won't release them. Never mind that all I want to do even now is just make a RAID-5 volume. I've never had such difficulty before.

Help?

---

### Post by scottac on 2010-10-05
been there man. mdadm is however a good raid option in my opinion. I have never had this specific problem, however assuming that you don't have any valuable data you could always zero the entire disk. I had to do that a couple of times before I figured out how to properly build and then mount the array's. 

Use this command to zero the disks:

```
dd if=/dev/zero of=/dev/hda bs=1M
```


Also. make sure you are setting up a configuration file prior to attempting to mount. I tried all the automated ways of doing this to no avail. So I finally just read the manual pages and wrote a an mdadm.conf file by hand.

One last thing. the array, dev/md0 must be in your etc/fstab for it to mount. Once it is all you need to do is run the command:

```
mount -a
```

if you would like to take a look at my etc/fstab or mdadm.conf just let me know. I can just share these files with you on google docs, or dropbox if you need me to.

Later,

Good luck man.

---

