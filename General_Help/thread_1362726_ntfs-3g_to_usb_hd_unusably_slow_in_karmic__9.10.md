---
title: "ntfs-3g to usb hd unusably slow in karmic / 9.10"
date: 2009-12-23
forum: General Help
---

### Post by eval- on 2009-12-23
Back again... the problem is ntfs-3g 2009.4.4.  If I remove ntfs-3g via synaptic then compile 2009.11.14 from source and install, my usb transfer rates are great!  However, if I do the same but compile 2009.4.4 from source, I have the exact same problem.  Let's pray that Lucid gets 2009.11.14!  teaser:

time cp -r Users/ /media/disk

real	0m53.151s
user	0m0.090s
sys	0m5.820s

Copying 1.5G to usb used take an hour with 2009.4.4!  Oy.

--------------
ORIGINAL POST:

Hi Everyone,

Last night I tried to back up 40g to an empty external usb HD.  I came back this morning to see 20g copied in over 12hrs.  There were no errors in dmesg or any of the logs.

This bug appears specific to ntfs-3g, and only happens when I copy to the external usb, not an ntfs partition on my local ssd.  I played with sync,async mount and pci= kernel options to no avail.  Also, mount.ntfs always consumes 90-100% CPU.

After beating my head against it all morning I finally tried using 'ntfsmount' and was able to copy 26g over usb in under an hour.  If ntfsmount is problematic and I should be using ntfs-3g, please let me know.  Or if anyone knows how to make ntfs-3g work at reasonably speeds over usb, speak up!  (The effect is most pronounced with many (small?) files, differences in copying one file appear small, see 'dd' results below PS)

Time permitting we'll try upgrading to ntfs-3g 2009.11.14 and if that fails we'll consider using Paragon's driver.  I do not know if this is an Ubuntu-specific bug or whether it appears in other distros, but it sure seems like a lot of recent posts have been related to slow usb transfers.  Perhaps some are ntfs-3g related, and we could use ntfsmount until ntfs-3g is fixed?  cheers,

eval-


PS.  Here is a test case I ran and various system details:

root@xuphoria:/win# ntfsmount /dev/sdb1 /media/disk -o async
root@xuphoria:/win# mount | grep sdb1
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,default_permissions,allow_other,blksize=4096,user=root)
root@xuphoria:/win# du -sh Users/
1.5G	Users/
root@xuphoria:/win# time cp -r Users/ /media/disk/

real	0m42.842s
user	0m0.130s
sys	0m5.280s
root@xuphoria:/win# du -sh /media/disk/Users/
1.5G	/media/disk/Users/
root@xuphoria:/win# rm -rf /media/disk/Users/
root@xuphoria:/win# umount /media/disk

root@xuphoria:/win# mount /dev/sdb1 /media/disk -o async
root@xuphoria:/win# mount | grep sdb1
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
root@xuphoria:/win# time cp -r Users/ /media/disk/

real	60m29.711s
user	0m0.140s
sys	0m5.610s
root@xuphoria:/win# du -sh /media/disk/Users/
1.5G	/media/disk/Users/


top (during ntfs-3g cp):

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3781 root      20   0 17820 2592  660 R  100  0.1  57:39.92 mount.ntfs


top (during ntfsmount cp):

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4012 root      20   0 25716 2160  664 D   18  0.1   0:16.31 ntfsmount      


dd:

root@xuphoria:~# mount /dev/sdb1 /media/disk -o async,rw,nosuid
root@xuphoria:~# dd if=/dev/zero of=/media/disk/test bs=4K count=200K
204800+0 records in
204800+0 records out
838860800 bytes (839 MB) copied, 19.8574 s, 42.2 MB/s
root@xuphoria:~# dd if=/dev/zero of=/media/disk/test bs=8K count=100K
102400+0 records in
102400+0 records out
838860800 bytes (839 MB) copied, 18.5498 s, 45.2 MB/s
root@xuphoria:~# umount /media/disk

root@xuphoria:~# ntfsmount /dev/sdb1 /media/disk -o async,rw,nosuid
root@xuphoria:~# dd if=/dev/zero of=/media/disk/test bs=4K count=200K
204800+0 records in
204800+0 records out
838860800 bytes (839 MB) copied, 14.2289 s, 59.0 MB/s
root@xuphoria:~# dd if=/dev/zero of=/media/disk/test bs=8K count=100K
102400+0 records in
102400+0 records out
838860800 bytes (839 MB) copied, 13.4743 s, 62.3 MB/s


infos:

root@xuphoria:~# uname -a
Linux xuphoria 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

root@xuphoria:~# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2646 MB in  2.00 seconds = 1323.86 MB/sec
 Timing buffered disk reads:   92 MB in  3.00 seconds =  30.66 MB/sec

root@xuphoria:~# ntfs-3g --version
ntfs-3g 2009.4.4 external FUSE 27

root@xuphoria:~# aptitude show ntfsprogs | grep Ver
Version: 2.0.0-1ubuntu3


dmesg:
[  113.930060] usb 2-2: new high speed USB device using ehci_hcd and address 3
[  114.098277] usb 2-2: configuration #1 chosen from 1 choice
[  114.115825] Initializing USB Mass Storage driver...
[  114.116033] scsi6 : SCSI emulation for USB Mass Storage devices
[  114.116260] usbcore: registered new interface driver usb-storage
[  114.116264] USB Mass Storage support registered.
[  114.117008] usb-storage: device found at 3
[  114.117012] usb-storage: waiting for device to settle before scanning
[  119.110334] usb-storage: device scan complete
[  119.111168] scsi 6:0:0:0: Direct-Access     ST350064 1NS                   PQ: 0 ANSI: 2 CCS
[  119.111872] sd 6:0:0:0: Attached scsi generic sg1 type 0
[  119.120592] sd 6:0:0:0: [sdb] 1953546336 512-byte logical blocks: (1.00 TB/931 GiB)
[  119.121421] sd 6:0:0:0: [sdb] Write Protect is off
[  119.121426] sd 6:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  119.121430] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  119.132256] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  119.132264]  sdb: sdb1
[  119.148899] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  119.148907] sd 6:0:0:0: [sdb] Attached SCSI disk

---

