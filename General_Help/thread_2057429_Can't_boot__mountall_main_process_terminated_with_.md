---
title: "Can't boot / mountall main process terminated with status 127"
date: 2012-09-13
forum: General Help
---

### Post by lordhedgehog on 2012-09-13
I don't recall the last time I rebooted this machine, but it wasn't long ago and I don't think I made any many changes to it since then. I do recall doing an apt-get upgrade and seeing something about ureadahead requiring a reboot, so I rebooted, and now the system doesn't boot up.

In normal mode, sometimes grub goes directly to a black screen, once in a blue moon it boots, but usually it hangs on boot.

In recovery mode, sometimes it hangs on boot with the same error that normal mode gives, but normally it boots. If I resume boot from recovery mode, it works fine. fsck found a bunch of deleted inodes and repaired them, but the problem didn't go away.

This appears to happen before the drive is mounted rw, because I can't find this is any log, but here's what I get in screen:

[] sd 4:0:0:0: [sda] Attached SCSI disk
[] GPT: disk_guids don't match
[] GPT: partition_entry_array_crc32 values don't match: 0x1e49ef79 != 0x9561ec81
[] GPT: Use GNU Parted to correct GPT errors.
[] sdb: sdb1 sdb2 sdb3
[] sd 5:0:0:0: [sdb] Attached SCSI disk
[] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[] mount: mounting /proc on /root/proc failed: No such file or directory
[] init: Error while reading from descriptor: Bad file descriptor
[] bin/sh: 0: Can't open /proc/self/fd/9
[] init: mountall main process (286) terminated with status 127
 
It looks like it's failing to mount /dev/sda (/dev/sda2 is my root directory). I don't understand the GPT error, and I don't know why it's not mounting. Any clues?

---

### Post by lordhedgehog on 2012-09-13
I believe I have solved the issue. The problem was created earlier than expected when I used dd to back up the system. Both hard drives had identical partitions with identical UUIDs, and on boot the system would arbitrarily read one drive or the other, which lead to the erratic behavior.

These commands appear to have fixed the issue:

sudo tune2fs -U random /dev/sdb1
sudo tune2fs -U random /dev/sdb2

---

