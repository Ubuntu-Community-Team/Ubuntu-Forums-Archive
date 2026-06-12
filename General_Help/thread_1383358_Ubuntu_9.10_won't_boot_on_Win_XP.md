---
title: "Ubuntu 9.10 won't boot on Win XP"
date: 2010-01-17
forum: General Help
---

### Post by madwoollything on 2010-01-17
Help!

When I try to boot into Ubuntu using Wubi on a windows XP host I'm left at a command prompt in grub which looks like 'sh:grub>' and have no real idea how to fix this.

I've found lots in various forums and the following  bug in launchpad which seems to suggest that this has been fixed Bug #477169 - however I have no idea how to implement the fix and what to do at the sh:grub> prompt.

Can someone please explain in simple steps what I need to do to recover so I can again boot into Ubuntu?

I've tried:
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot

The system starts to boot and then just hangs. Here are some of the messages that appear:

RAMDISK: Couldn't find valid RAM disk image starting at 0.
List of all partitions:
0800 156290904 sda driver: sd
0801 152031600 sda1
0802 4248576 sda2
No filesystem could mount rott, tried: ext3 ext2 ext4 fuseblk
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
Pid: 1, comm: swapper Not tainted 2.6.31-14-generic #48-Ubuntu
Call Trace:
.
.
.

 I'm guessing that this is unrecoverable and that this is the end of Ubuntu on this system?

---

### Post by madwoollything on 2010-01-22
Found fix in launchpad bug #477104.
I downloaded the wubildr file and replaced it in the C:\Ubuntu dir as in #90

I didn't modify anything else. Everything seems to work. Brilliant!!

---

### Post by Saiko Berry on 2010-01-22
Careful when updating Wubi's grub through update center. Weird things happen.

---

