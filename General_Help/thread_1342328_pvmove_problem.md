---
title: "pvmove problem"
date: 2009-11-30
forum: General Help
---

### Post by CyberMonk6 on 2009-11-30
I have a frightening problem after a recent attempt at move from a RAID-5 to a RAID-6 (using mdadm) with the help of LVM.
I'm running on Ubuntu 9.04, currently with one degraded RAID-5 and one degraded RAID-6 (both still operational).

I followed this process: [http://www.fedoraforum.org/forum/showthread.php?t=213698](http://www.fedoraforum.org/forum/showthread.php?t=213698)

However, I was forced to force one of the steps using the -ff option because of an error that
I unfortunately don't recall. (It was either vgextend /dev/vg0 /dev/md1 or pvmove -v /dev/md0 that needed to be forced,
but the move took so long that I no longer remember which it was.) I don't know that I should have, however, as the
pvmove process is now failing to complete, and I'm stumped.

My setup is one volume group (vg0), which formerly had only one physical volume (/dev/md0), but to which I added
the degraded RAID-6 (/dev/md1) for the process in the above-linked post.  I had to force the a step, as mentioned--if
I recall, the error that required the force referenced a duplicate name or something like that--but afterward pvmove seemed
to be going alright.  However, pvmove now seems to be going awry.  On a fresh boot, when I issue "sudo pvmove -v /dev/md0",
here's the message I receive:

File descriptor 5 left open
    Finding volume group "vg0"
  Detected pvmove in progress for /dev/md0
    Found volume group "vg0"
    Found volume group "vg0"
    Found volume group "vg0"
    Checking progress every 15 seconds
  /dev/md0: Moved: 100.0%
    Updating volume group metadata
    Creating volume group backup "/etc/lvm/backup/vg0" (seqno 1346).
    Found volume group "vg0"
    Found volume group "vg0"
    Suspending vg0-backup (252:1) with device flush
    Suspending vg0-pvmove0 (252:0) with device flush
    Found volume group "vg0"
    Found volume group "vg0"
    Suspending vg0-data (252:2) with device flush
    Found volume group "vg0"
    Found volume group "vg0"
    Found volume group "vg0"
    Loading vg0-pvmove0 table
    Suppressed vg0-pvmove0 identical table reload.
    Resuming vg0-pvmove0 (252:0)
    Found volume group "vg0"
    Loading vg0-pvmove0 table
    Suppressed vg0-pvmove0 identical table reload.
    Loading vg0-backup table
    Suppressed vg0-backup identical table reload.
    Resuming vg0-backup (252:1)
    Found volume group "vg0"
    Loading vg0-pvmove0 table
    Suppressed vg0-pvmove0 identical table reload.
    Loading vg0-data table
    Suppressed vg0-data identical table reload.
    Resuming vg0-data (252:2)

This repeats indefinitely until the system finally seems to be unable to handle it (a "ps -A" shows a huge number of
processes named "lvm").  vg0-data is actually available for a little bit upon booting at its mounted point of /media/data,
and vg0-backup doesn't seem to be mounted any longer, but after a few minutes I can no longer access vg0-data
(presumably because some process here is going crazy).

In any case, I'm very much a novice here, and any help would be sincerely appreciated.  The fact that I can still access
my data, if only for a short while on a fresh boot, is heartening, but I'm worried about losing data.  Thanks in advance for
any assistance, and let me know if I've left out any needed information.

---

### Post by CyberMonk6 on 2009-11-30
No one has any ideas and/or experience with this? :(

---

