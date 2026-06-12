---
title: "urgent help with usb stick data recovery"
date: 2011-05-07
forum: General Help
---

### Post by John Krow on 2011-05-07
Need urgently to recover a .rtf file created with open office, on a laptop running Ubuntu Karmic as a live cd. The .rtf was saved on a usb memory stick, then the laptop lid closed. On rebooting, the usb stick is no longer visible in nautilus.

Am working with stick now on my desktop running Lucid.
have tried a number of tools to recover data but inexperienced. The data is needed urgently, please help.

Ok so the output of 
```

$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID ba57:1001  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```and when plugging in the usb stick
```
$ sudo tail -f /var/log/messages
May  7 23:07:13 nest-desktop kernel: [ 6235.892529] usb 1-7: new high speed USB device using ehci_hcd and address 5
May  7 23:07:13 nest-desktop kernel: [ 6236.025002] usb 1-7: configuration #1 chosen from 1 choice
May  7 23:07:13 nest-desktop kernel: [ 6236.032877] scsi9 : SCSI emulation for USB Mass Storage devices
May  7 23:07:18 nest-desktop kernel: [ 6241.052498] scsi 9:0:0:0: Direct-Access     USB      Flash Drive      1.00 PQ: 0 ANSI: 2
May  7 23:07:18 nest-desktop kernel: [ 6241.053120] sd 9:0:0:0: Attached scsi generic sg2 type 0
May  7 23:07:18 nest-desktop kernel: [ 6241.061725] sd 9:0:0:0: [sdb] 11 512-byte logical blocks: (5.63 kB/5.50 KiB)
May  7 23:07:18 nest-desktop kernel: [ 6241.062216] sd 9:0:0:0: [sdb] Write Protect is off
May  7 23:07:18 nest-desktop kernel: [ 6241.065602]  sdb: unknown partition table
May  7 23:07:18 nest-desktop kernel: [ 6241.080978] sd 9:0:0:0: [sdb] Attached SCSI removable disk

``````
fdisk -l
```gives no output in the terminal
I will post any further info as it emerges...any ideas?

---

### Post by John Krow on 2011-05-07
I have an idential usb stick, having a go with ddrescue

```
crow@nest-desktop:~$ sudo ddrescue -v /dev/sdb /dev/sdc logfile


About to copy 5632 Bytes from /dev/sdb to /dev/sdc
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Max_retries: 0    
Direct: no    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:      5632 B,  errsize:       0 B,  current rate:        0 B/s
   ipos:       512 B,   errors:       0,    average rate:        0 B/s
   opos:       512 B,     time from last successful read:       0 s
Finished 
```but cannot see anything on the destination stick (in nautilus).

---

### Post by John Krow on 2011-05-08
```
crow@nest-desktop:~$ sudo sfdisk -l -f /dev/sdb

Disk /dev/sdb: 11 cylinders, 1 heads, 1 sectors/track

sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/sdb: unrecognised partition table type
No partitions found
```

---

### Post by John Krow on 2011-05-08
given up on this but learned a lot. ```
crow@nest-desktop:~$ sudo mount -t vfat -o loop,ro,noexec flashdisk.dd /mnt
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

crow@nest-desktop:~$ dmesg|tail
[  248.211377] wlan0: RX AssocResp from e8:be:81:75:97:bc (capab=0x411 status=0 aid=2)
[  248.211381] wlan0: associated
[ 3374.964070] Program strings tried to access /dev/mem between 101000->102000.
[ 3405.482710] Program strings tried to access /dev/mem between 101000->102000.
[ 3496.698965] Program strings tried to access /dev/mem between 101000->102000.
[ 4101.154508] VFS: Can't find an ext2 filesystem on dev loop0.
[ 4151.258896] VFS: Can't find an ext2 filesystem on dev loop0.
[ 4160.502809] VFS: Can't find ext3 filesystem on dev loop0.
[ 4606.315369] FAT: bogus number of FAT structure
[ 4606.315375] VFS: Can't find a valid FAT filesystem on dev loop0.
```

---

