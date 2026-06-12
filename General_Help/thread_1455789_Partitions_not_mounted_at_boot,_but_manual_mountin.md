---
title: "Partitions not mounted at boot, but manual mounting works fine"
date: 2010-04-16
forum: General Help
---

### Post by GeoMX on 2010-04-16
We have a read-only Linux system (I've set it up following these instructions: [http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/](http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/)), we have one disk with four partitions, one for all system files (/), a swap partition and two extra partitions for configuration media files.

The /etc/fstab contains only the last two partitions and I'm using UUID for referring the devices.

The problem I'm facing is, when testing the system with one motherboard, everything works perfect, both extra partitions are mounted at boot time. But when using another motherboard (same model than the previous), the extra partitions do not mount at boot, they can be mounted manually running mount command, but have no clue why they can't be mounted at boot. For a SATA disk, only one extra partitions is mounted at boot, testing with an IDE, both partions are not mounted.

I can't figure out what the problem may be, could you please provide me with some information on how the mount process at boot works? What are the log files I could search for related warning/error messages?

For the moment, I'm thinking of executing a mount instruction after booting the system, but would like to find out what causes the system not to mount those partitions.

More info:
I'm using Ubuntu Karmic, partitions are ext4, I created them manually running parted with parameters, when checking the disk I get messages regarding partitions not ending on cylinder limits.

Thanks in advance for all of your help.

---

### Post by mk1w86 on 2010-04-16
So to clarify, you are using the same hard drive but swapping it between two identical motherboards?

Could you please post your fstab?

For logs you could run:

```
dmesg
```

and check /var/log/syslog

If/when you find the relevant information in the logs can you post that as well?

---

### Post by GeoMX on 2010-04-16
Thanks for your reply.

> **mk1w86 said:**
> So to clarify, you are using the same hard drive but swapping it between two identical motherboards?

Yes, I plug a new disk to my system (running Karmic), create a clean/light Karmic installation using debootstrap/chroot and then I take this new disk to its own system.

After posting my message I  tried dmesg but could not find anything related to the mount problems.

I found the problem when pluggin another disk with a "normal" Linux installation (no read-only), the system could not boot because fsck returned some errors and finished showing a mainteinance shell, this is what appeared on screen:

> 
fsck from util-linux-ng 2.16
/dev/sda1: Superblock last mount time (Fri Apr 16 10:22:07 20010, now = Sun Aug 23 14:38:00 2009) is in the future.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i. e., without -a or -p options)
mountall: fsck / [462] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (454) terminated with status 3
A mainteinance shell will now be started.
CONTROL-D will terminate this shell and retry
root@systemname: ~#


Running fsck manually fixed the inconsistency for this disk, configuring motherboard's date/time allowed all partitions in the first disk to mount correctly at boot time.

I think the same messages appeared for the extra partitions in first disk but the system could still boot because of the script that merges / as an union file system, but I could not see start up messages for the read-only system because GRUB is configured to hide them and I was not able alter this configuration. Do you know if start up messages are stored somewhere or they only appear on screen? Are they stored in syslog?

I've never imagined having a wrong date/time would cause a problem like this one, I'm having lots of fun with Linux these days ;).

---

### Post by mikewhatever on 2010-04-16
```
dmesg > ~/Desktop/dmesg.txt
```

Then look for dmesg.txt file on your desktop and post it here.

---

### Post by GeoMX on 2010-04-16
Sorry mikewhatever, I was editing my previous post while you were posting your reply. I already found the problem, it was the difference between the new motherboard's date/time and the one stored in the disk for its last mount/file check that was causing the partitions not to be mounted at boot, I detail it on my previous post.

---

### Post by mikewhatever on 2010-04-16
Glad you got it solved.

---

