---
title: "Cannot manually dock iPod"
date: 2011-06-12
forum: General Help
---

### Post by realdeal_55 on 2011-06-12
Hey, Ubuntu forum folk! :-D

I set my friend up with Ubuntu (11.04) on her laptop. I'm having some trouble  getting her iPod (8GB 4th- or 5th-gen iPod Nano) to mount so she can sync it with Banshee and we could use your expert assistance. When I  plug it in, I get the following error:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```syslog shows the following at the time when I plug in the iPod:

```
Jun 12 00:36:35 brittany-Satellite-A210 kernel: [ 3617.728103] usb 1-1: new high speed USB device using ehci_hcd and address 6
Jun 12 00:36:35 brittany-Satellite-A210 kernel: [ 3617.867163] scsi9 : usb-storage 1-1:1.0
Jun  12 00:36:36 brittany-Satellite-A210 kernel: [ 3618.866566] scsi  9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Jun 12 00:36:36 brittany-Satellite-A210 kernel: [ 3618.869824] sd 9:0:0:0: Attached scsi generic sg2 type 0
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3618.873314] sd 9:0:0:0: [sdb] Spinning up disk....ready
Jun  12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.277161] sd 9:0:0:0:  [sdb] 1946049 4096-byte logical blocks: (7.97 GB/7.42 GiB)
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.277755] sd 9:0:0:0: [sdb] Write Protect is off
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.277766] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.279127] sd 9:0:0:0: [sdb] No Caching mode page present
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.279138] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun  12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.281737] sd 9:0:0:0:  [sdb] 1946049 4096-byte logical blocks: (7.97 GB/7.42 GiB)
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.283503] sd 9:0:0:0: [sdb] No Caching mode page present
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.283514] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.401651]  sdb: [mac] sdb1 sdb2
Jun  12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.408077] sd 9:0:0:0:  [sdb] 1946049 4096-byte logical blocks: (7.97 GB/7.42 GiB)
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.410153] sd 9:0:0:0: [sdb] No Caching mode page present
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.410164] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 12 00:36:38 brittany-Satellite-A210 kernel: [ 3620.410175] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Jun 12 00:36:40 brittany-Satellite-A210 kernel: [ 3622.004101] sd 9:0:0:0: [sdb] Bad block number requested
Jun 12 00:36:40 brittany-Satellite-A210 kernel: [ 3622.004227] hfs: unable to find HFS+ superblock
Jun 12 00:36:40 brittany-Satellite-A210 kernel: [ 3622.664077] sd 9:0:0:0: [sdb] Bad block number requested
Jun 12 00:36:40 brittany-Satellite-A210 kernel: [ 3622.664127] hfs: unable to find HFS+ superblock
```I did some research on the error message and tried the following in a terminal:

```
sudo mount -t vfat /dev/sdb2 /media/iPod
```(I had to use sudo mkdir /media/iPod to create that mount point, first)

which returns the exact same error message as above. Syslog, however, shows something new after that:

```
Jun 12 00:30:00 brittany-Satellite-A210 kernel: [ 3222.212700] FAT: bogus number of reserved sectors
Jun 12 00:30:00 brittany-Satellite-A210 kernel: [ 3222.212715] VFS: Can't find a valid FAT filesystem on dev sdb2.
```The syslog  error seems to imply that the iPod's filesystem is broken or  nonexistant, but there's definitely music on there, already, and it  plays fine. That, or the iPod uses a different type of fileysystem,  which means I've got no clue what to enter into terminal. :-P That's  as far as I've gotten, and I'm stuck. Do you have any ideas? I asked a friend who suggested I install Wine and iTunes so my friend can sync her iPod that way, but I'd like to keep things as simple as possible for my friend. 

Please and thanks! :-D

---

