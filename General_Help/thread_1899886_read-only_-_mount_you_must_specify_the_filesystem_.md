---
title: "read-only - mount: you must specify the filesystem type"
date: 2011-12-24
forum: General Help
---

### Post by zac2290 on 2011-12-24
I have no idea how this happened, but the entire system is read-only now. I have scoured forums and tried remounting the drive to no avail.

I have tried:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9572

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      116680   937224192   83  Linux
/dev/sda2          116680      121602    39535617    5  Extended
/dev/sda5          116680      121602    39535616   82  Linux swap / Solaris

```

and then:
```
mount -o remount, -rw /dev/sda1 /
```
(also tried sda2 and sda5 just in case)

but keep getting:
```
mount: you must specify the filesystem type
```

All I want to do is be able to write files again! Please help!

---

### Post by WorMzy on 2011-12-24
Are you sure that the filesystem is read-only? What does

```
mount
```

say?

Also, what does fstab say?

```
cat /etc/fstab
```

---

### Post by zac2290 on 2011-12-24
Thank you for your reply. I am relatively new to linux so bear with me..

```
root@ubuntu:~# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ac102a54-2e7d-466e-bcf2-091854e3c305 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1cdd963e-9fc4-4485-b95b-e2970fb083dc none            swap    sw              0       0

```

---

### Post by WorMzy on 2011-12-24
Alright, that suggests that the filesystem is initially being mounted as rw, but is being remounted ro, presumably due to an error.

Can you post the output of

```
dmesg | tail -30
```

Also, do you have a liveCD or liveUSB handy? (like the one you used to install Ubuntu)

---

### Post by zac2290 on 2011-12-24
The server is collocated, and we had the colo install ubuntu, which had to have been done via USB as the server has no CD drive.

Thanks again for your help.. I really appreciate it

```
dmesg | tail -30
[35859.731976] ata1: EH complete
[35861.552497] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[35861.552500] ata1.00: irq_stat 0x40000008
[35861.552502] ata1.00: failed command: READ FPDMA QUEUED
[35861.552507] ata1.00: cmd 60/08:00:a0:1f:80/00:00:02:00:00/40 tag 0 ncq 4096 in
[35861.552508]          res 41/40:00:a6:1f:80/00:00:02:00:00/40 Emask 0x409 (media error) <F>
[35861.552511] ata1.00: status: { DRDY ERR }
[35861.552512] ata1.00: error: { UNC }
[35861.557727] ata1.00: configured for UDMA/133
[35861.557736] sd 0:0:0:0: [sda] Unhandled sense code
[35861.557737] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[35861.557740] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[35861.557744] Descriptor sense data with sense descriptors (in hex):
[35861.557746]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[35861.557753]         02 80 1f a6
[35861.557757] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[35861.557760] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 02 80 1f a0 00 00 08 00
[35861.557768] end_request: I/O error, dev sda, sector 41951142
[35861.557778] EXT4-fs error (device sda1): __ext4_get_inode_loc:
[35861.557782] ata1: EH complete
[35861.557784] unable to read inode block - inode=1322318, block=5243636
[35863.377478] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[35863.377481] ata1.00: irq_stat 0x40000008
[35863.377484] ata1.00: failed command: READ FPDMA QUEUED
[35863.377489] ata1.00: cmd 60/08:00:a0:1f:80/00:00:02:00:00/40 tag 0 ncq 4096 in
[35863.377490]          res 41/40:00:a6:1f:80/00:00:02:00:00/40 Emask 0x409 (media error) <F>
[35863.377492] ata1.00: status: { DRDY ERR }
[35863.377494] ata1.00: error: { UNC }
[35863.382680] ata1.00: configured for UDMA/133
[35863.382685] ata1: EH complete

```

---

### Post by WorMzy on 2011-12-24
Well, it looks like you have some minor filesystem corruption, which could probably be fixed by running fsck on the affected partition.

Unfortunately, you can't (or at least *shouldn't*) run fsck on a mounted filesystem, as that can cause more damage than it fixes. So you'll need to boot into a live environment (a liveUSB stick is fine, if that's what you have available), then run

```
sudo fsck /dev/sda1
```

Also, be aware that filesystem corruption may be caused by the disk being close to failing. You might want to take the opportunity to back up any important files before fscking.

---

### Post by zac2290 on 2011-12-26
Sorry for the delayed response, hope you had a Merry Christmas!

Is there any other way other than the USB method? The colo will charge some big bucks to set that up. And it doesn't seem to be anything I can do remotely.

Would a possible work around be to create a smaller partition, running a live environment from there to run the fsck?

Thanks

---

### Post by WorMzy on 2011-12-26
Sure. So long as the partition you want to fsck isn't mounted, you can fsck it from any Linux/Unix environment (so long as you have the necessary fsck tool available).

---

