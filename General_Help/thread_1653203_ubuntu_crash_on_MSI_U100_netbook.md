---
title: "ubuntu crash on MSI U100 netbook"
date: 2010-12-26
forum: General Help
---

### Post by mfeijen on 2010-12-26
Dear ubuntu community,

I'm running ubuntu netbook 10.10 beside windows xp home edition on my MSI Wind U100 netbook. I'm very satisfied with it (!)

Unfortenatly ubuntu just crashed, eg, it doesnt want to start up again. What happened: under ubuntu I tried to connect the netbook with an external (philips) monitor (via VGA) and the ubuntu os gut stuck every time. So I resetted the OS by means of the power button - and at the last reset ubuntu crashed (but Windows still works!) and did not wanto start up again anymore.  I tried 3 options (I-III):

I- when restarting and selecting unbuntu (on top of grublist)I only get a black screen displaying the following:

"No init found. Try passing init = bootarg"
"(initramfs)"

II When I restart and select Ubuntu in recovery mode, a black screens appears displaying:

"gave up waiting for root device. Common problem:"
  "-boot args"
  "-missing modules"
"ALERT! /dev/disk/by-uuid/86d5bd22-1dee/4526/bc94/c8083de7070a does not exist"
"Busybox v1.153 (ubuntu 1:1 153-ubuntu5 built in shell ash"

III- when I try to reinstall ubuntu netbook 10.10 with the usb stick (same one that I used for the first installation), the installation gets stuck as well once I choose Installation.

Can anybody please help me? - providing the easiest option bearing in mind I'm an ubuntu amateur;) I have made a back up of all personal data.

UPDATE: After some googling on this matter I did try to use the e2fsck command but that doesnt work - the log below:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  12  Compaq diagnostics
/dev/sda2   *         511        5610    40965750    7  HPFS/NTFS
/dev/sda3            5611       12554    55770558    7  HPFS/NTFS
/dev/sda4           12554       19458    55456769    5  Extended
/dev/sda5           12554       19446    55363584   83  Linux
/dev/sda6           19446       19458       92160   82  Linux swap / Solaris

Disk /dev/sdb: 2041 MB, 2041577472 bytes
129 heads, 32 sectors/track, 965 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a394e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         966     1993712    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(973, 128, 32) logical=(965, 122, 32)
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda4
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?


Many thanks in advance (!)

Kind regards;)
M Feijen

---

