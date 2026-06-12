---
title: "Ubuntu not starting"
date: 2012-07-27
forum: General Help
---

### Post by bamdl001 on 2012-07-27
If anyone can help on this, much appreciated... All of sudden like I am no longer able to load Ubuntu. There is story to this but this is only a hypothesis. My 4yo grandson slammed the lid down on my ACER laptop destroying the screen. I had the screen replaced but even the replacement screen has been going blank all of a sudden and has been doing so a number of times which meant I had to continually turn off my laptop and reboot. My theory is that like windows OS's, Ubuntu became corrupted and now I'm getting the following on my screen and can't get past this:

```
20
[ 2.815721] Code: 00 55 89 e5 89 c7 56 53 e8 c3 34 23 00 86 5f 04 68 ff ff ff ff 8b 77 08 cb 1c 8d b6 00 00 00 00 8b 0c 85 40 80 7a c0 86 57 14 <86> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 cc ef 59 c0 ba
[ 2.815721] EIP: [<e035e68a>] _ _percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f640 3d6c
[ 2.815721] CR2 00000000023b8000
[2.832167] --- [ end trace 585d55b05bf ce 579]---
Killed
mount: mounting /dev on /root/dev failed: no such file or directory.
mount: mounting /sys on /root/sys failed: no such file or directory.
mount: mounting /proc on /root/proc failed: no such file or directory.
Target file system doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1: 1.13.3-1ubuntu11) built-in shell  (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 6.300611 usb-storage: device scan complete
[ 6.3025911] scsi 6:0:0:0: Direct-Access  Generic-Multi-Card     1:00 PQ
: 0 ANSI: 0 CCS
[ 6.303147] sd 6:0:0:0: Attached scsi generic Sg3 type 0
[ 6.306816] sd 6:0:0:0: [sdc] Attached SCSI removable disk

(initramfs) _
```

Many Thanks

---

### Post by matt_symes on 2012-07-28
Hi

> EIP: [<e035e68a>] _ _percpu_counter_sum+0x2a/0x70 SS:E

Your kernel is crashing.

Anyway, to try to fix the boot issue, boot into a LiveCD/USB and run fsck on the root partition.

I believe you can do this from "disc utility" or from the command line.

```
sudo fsck /dev/sdXY
```

Where XY are the drive and the partition number that contains the root filing system.

If it's just a corrupted file system then that may let you boot into it.

Kind regards

---

