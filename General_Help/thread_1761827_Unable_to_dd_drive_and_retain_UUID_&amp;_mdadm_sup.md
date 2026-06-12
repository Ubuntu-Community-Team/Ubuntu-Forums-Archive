---
title: "Unable to dd drive and retain UUID &amp; mdadm superblock"
date: 2011-05-18
forum: General Help
---

### Post by User4519 on 2011-05-18
I'm experiencing the strangest thing...

I have an mdadm linear array of 4 500GB drives. One of them had a few bad sectors, so I've dd'ed it to a new one (conv=noerror), and tried to start my array.

Mdadm refuses, saying, "mdadm: /dev/md4 assembled from 3 drives - not enough to start the array."

This puzzled me, because I had diffed different samples from different positions on the source and the mirror drive and confirmed they were identical.

Checking the superblocks confirms three old drives still having their superblocks as expected, while the newly mirrored one has,

[FONT="Courier New"]daniel@lnxsrv:~$ sudo mdadm --misc --examine /dev/sdf1
mdadm: No md superblock detected on /dev/sdf1.[/FONT]

 - and,

[FONT="Courier New"]daniel@lnxsrv:~$ sudo blkid /dev/sdf1[/FONT]

(i.e. no output, no uuid there). fdisk -l shows the mirror having the same disk id as the source drive, and the partition table is sane,

[FONT="Courier New"]Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7238942

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect[/FONT]

Okay, so I stopped all mdadm arrays, unplugged all array drives, reconnected the mirror drive (now sdc) and popped the old source drive back into my USB to SATA bay adapter (became sdd), and did,

[FONT="Courier New"]daniel@lnxsrv:~$ sudo blkid /dev/sdc1
daniel@lnxsrv:~$ sudo blkid /dev/sdd1
/dev/sdd1: UUID="db5df182-a566-d728-7bd6-f7709fe2e456" TYPE="linux_raid_member"[/FONT] 

As before. The mirror apparently has no uuid, but the original does.

To confirm my sanity, I did,

[FONT="Courier New"]daniel@lnxsrv:~$ sudo dd bs=1M count=50 if=/dev/sdc of=./sdc && sudo dd bs=1M count=50 if=/dev/sdd of=./sdd && sudo diff -s sdc sdd
50+0 records in
50+0 records out
52428800 bytes (52 MB) copied, 0,631617 s, 83,0 MB/s
50+0 records in
50+0 records out
52428800 bytes (52 MB) copied, 1,60629 s, 32,6 MB/s
Files sdc and sdd are identical[/FONT]

WTF? Am I completely retarded here? How can the uuid not be the same when bit-for-bit from the very first byte of the drive, covering MFT etc., these two drives are identical according to diff?

Stomped here! :D Please help.

---

### Post by User4519 on 2011-05-18
Ouuuuchhhh!!!

I think I know what's going on. I'm forgetting that the mdadm superblock - IIUC - is **at the end of the drive**, yeah?

Check this out:

[FONT="Courier New"]daniel@lnxsrv:~$ sudo dd if=/dev/sdd of=/dev/sdc bs=1kB skip=499999000 seek=499999000 conv=noerror
dd: reading `/dev/sdd': Input/output error
105667+1 records in
105667+1 records out
105667136 bytes (106 MB) copied, 11,4988 s, 9,2 MB/s
dd: reading `/dev/sdd': Input/output error
105667+1 records in
105667+1 records out
105667136 bytes (106 MB) copied, 13,3232 s, 7,9 MB/s
dd: reading `/dev/sdd': Input/output error
105667+1 records in
105667+1 records out
105667136 bytes (106 MB) copied, 15,1313 s, 7,0 MB/s
dd: reading `/dev/sdd': Input/output error
105667+1 records in
105667+1 records out
105667136 bytes (106 MB) copied, 16,9478 s, 6,2 MB/s
dd: reading `/dev/sdd': Input/output error
105667+1 records in
105667+1 records out
105667136 bytes (106 MB) copied, 18,7639 s, 5,6 MB/s
108857+2 records in
108857+2 records out
108857696 bytes (109 MB) copied, 19,3975 s, 5,6 MB/s
daniel@lnxsrv:~$ sudo partprobe 
daniel@lnxsrv:~$ sudo blkid /dev/sdc1
daniel@lnxsrv:~$ sudo blkid /dev/sdd1
/dev/sdd1: UUID="db5df182-a566-d728-7bd6-f7709fe2e456" TYPE="linux_raid_member"[/FONT]

There're bad sectors at the veeeery end of the drive. And, dd skips BLOCKSIZE every time it hits an error. My previous dd run was with 1M blocks, above is an attempt with 1k blocks, and apparently that still skips the actual superblock area. Talk about a corner case here!!! LOL :D

I'm not even sure that 1k block sizes are even possible? Isn't the kernel minimum size like 4k or something? ... I'm gonna try decreasing the block size to 512 bytes, though, and report back :)

---

### Post by User4519 on 2011-05-18
Okay, 512-byte blocks in dd was possible, but it didn't help (did give twice the number of errors, though ;) ).

Also, the last three MB are clear copied correctly, so know I'm thinking this may not be the problem anyway?

Grrr... Still looking for help :)

---

### Post by User4519 on 2011-05-18
Bump?

---

### Post by dcstar on 2011-05-19
> **DanielBuus said:**
> I'm experiencing the strangest thing...

I have an mdadm linear array of 4 500GB drives. One of them had a few bad sectors, so I've dd'ed it to a new one (conv=noerror)
.........

Use **ddrescue** for bad drives.

---

### Post by User4519 on 2011-05-19
> **dcstar said:**
> Use **ddrescue** for bad drives.

David, thank you! I just ran dd_rescue on the last handful of megabytes of the drive, and success!:

[FONT="Courier New"]daniel@lnxsrv:~$ sudo dd_rescue -s 499999800000 /dev/sde /dev/sdc
dd_rescue: (info): ipos: 488383464.0k, opos: 488383464.0k, xferd:    102409.3k
                *  errs:      0, errxfer:         0.0k, succxfer:    102409.3k
             +curr.rate:        5kB/s, avg.rate:     7612kB/s, avg.load:  3.3%
dd_rescue: (warning): /dev/sde (488383464.0k): Input/output error!

dd_rescue: (info): ipos: 488383464.5k, opos: 488383464.5k, xferd:    102409.8k
                *  errs:      1, errxfer:         0.5k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     6707kB/s, avg.load:  2.9%
dd_rescue: (warning): /dev/sde (488383464.5k): Input/output error!

dd_rescue: (info): ipos: 488383465.0k, opos: 488383465.0k, xferd:    102410.3k
                *  errs:      2, errxfer:         1.0k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     5997kB/s, avg.load:  2.6%
dd_rescue: (warning): /dev/sde (488383465.0k): Input/output error!

dd_rescue: (info): ipos: 488383465.5k, opos: 488383465.5k, xferd:    102410.8k
                *  errs:      3, errxfer:         1.5k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     5423kB/s, avg.load:  2.4%
dd_rescue: (warning): /dev/sde (488383465.5k): Input/output error!

dd_rescue: (info): ipos: 488383466.0k, opos: 488383466.0k, xferd:    102411.3k
                *  errs:      4, errxfer:         2.0k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     4949kB/s, avg.load:  2.2%
dd_rescue: (warning): /dev/sde (488383466.0k): Input/output error!

dd_rescue: (info): ipos: 488383466.5k, opos: 488383466.5k, xferd:    102411.8k
                *  errs:      5, errxfer:         2.5k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     4551kB/s, avg.load:  2.0%
dd_rescue: (warning): /dev/sde (488383466.5k): Input/output error!

dd_rescue: (info): ipos: 488383467.0k, opos: 488383467.0k, xferd:    102412.3k
                *  errs:      6, errxfer:         3.0k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     4211kB/s, avg.load:  1.9%
dd_rescue: (warning): /dev/sde (488383467.0k): Input/output error!

dd_rescue: (info): ipos: 488383467.5k, opos: 488383467.5k, xferd:    102412.8k
                *  errs:      7, errxfer:         3.5k, succxfer:    102409.3k
             +curr.rate:        0kB/s, avg.rate:     3920kB/s, avg.load:  1.8%
dd_rescue: (warning): /dev/sde (488383467.5k): Input/output error!

dd_rescue: (info): ipos: 488386526.7k, opos: 488386526.7k, xferd:    105472.0k
                   errs:      8, errxfer:         4.0k, succxfer:    105468.0k
             +curr.rate:     5382kB/s, avg.rate:     3951kB/s, avg.load:  1.8%
dd_rescue: (info): /dev/sde (488386584.0k): EOF
Summary for /dev/sde -> /dev/sdc:
dd_rescue: (info): ipos: 488386584.0k, opos: 488386584.0k, xferd:    105529.3k
                   errs:      8, errxfer:         4.0k, succxfer:    105525.3k
             +curr.rate:     1224kB/s, avg.rate:     3946kB/s, avg.load:  1.8%
daniel@lnxsrv:~$ sudo sync
daniel@lnxsrv:~$ sudo blkid /dev/sdc1
/dev/sdc1: UUID="db5df182-a566-d728-7bd6-f7709fe2e456" TYPE="linux_raid_member" 
daniel@lnxsrv:~$ sudo blkid /dev/sde1
/dev/sde1: UUID="db5df182-a566-d728-7bd6-f7709fe2e456" TYPE="linux_raid_member"[/FONT]

Woooh! :D Perfect timing for starting a Scrub on the overlying ZFS-FUSE array. Just ordered a new mobo and processor, will be arriving in 24 hrs :P

Thanks again!

---

