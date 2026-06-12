---
title: "Weird External HD Problem"
date: 2010-04-25
forum: General Help
---

### Post by nabarge on 2010-04-25
I just got a new Hitachi 1 GB external USB HD. I plan on using to store media and video files. But I have been having trouble getting it to work properly. It mounts fine and I can copy some files to the drive, but anything thats too large (more than 100MB it seems) and the HD will blink for a few seconds, copy about 100 MB of the file and then the indicator lights shut off. In nautilus the progress bar hangs for 30 seconds and then I get an input output error. I thought it might be an issue of the drive format being fat, so I reformatted it to ext3, but same deal. I tested the drive on my mac and I works normally so the drive seems to be fine (I actually copied the files from my Ubuntu machine over the network to the drive, so i don't think the files are corrupt). 

I am currently running "Ubuntu 10.04 LTS", so would this be some beta bug maybe or has anyone else seen this happen? Any help would be much appreciated, thanks!

---

### Post by scouser73 on 2010-04-25
Try and format it to NTFS and see if you still encounter the problem, although that shouldn't really matter what the filesystem is set to.

---

### Post by srs5694 on 2010-04-25
Try the following commands, and post their output, shortly after the problem occurs:

```

dmesg | tail
tail /var/log/messages
sudo fdisk -l

```

There may be error codes buried in there somewhere.

I suspect there's something flaky about the drive's USB interface -- something strange that works differently under OS X vs. Linux.

---

### Post by efflandt on 2010-04-26
Do you have a power supply connected to the drive or cable with double USB connectors?  Maybe it is not getting enough 5 VDC from USB on that computer.

---

### Post by nabarge on 2010-04-26
thanks for the quick replies. So it does have a separate power supply so that "shouldn't" be the problem. I have attempted this with an ntfs formatting same problem. 

I tried again today the error message says "There was an error copying the file into /media/DVDHD." and under more details: "Error splicing file: No space left on device".
(but in reality there is plenty of space)

this is the output of the above commands:

```
nikbarge@LinuxBox:~$ dmesg | tail
[86103.956129] VFS: busy inodes on changed media or resized disk sr0
[86105.955325] VFS: busy inodes on changed media or resized disk sr0
[86105.955475] VFS: busy inodes on changed media or resized disk sr0
[86105.955525] VFS: busy inodes on changed media or resized disk sr0
[86107.955665] VFS: busy inodes on changed media or resized disk sr0
[86107.955720] VFS: busy inodes on changed media or resized disk sr0
[86107.955861] VFS: busy inodes on changed media or resized disk sr0
[86109.955817] VFS: busy inodes on changed media or resized disk sr0
[86109.955871] VFS: busy inodes on changed media or resized disk sr0
[86109.956028] VFS: busy inodes on changed media or resized disk sr0
nikbarge@LinuxBox:~$ tail /var/log/messages
Apr 26 16:00:17 LinuxBox kernel: [86103.956129] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:19 LinuxBox kernel: [86105.955325] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:19 LinuxBox kernel: [86105.955475] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:19 LinuxBox kernel: [86105.955525] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:21 LinuxBox kernel: [86107.955665] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:21 LinuxBox kernel: [86107.955720] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:21 LinuxBox kernel: [86107.955861] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:23 LinuxBox kernel: [86109.955817] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:23 LinuxBox kernel: [86109.955871] VFS: busy inodes on changed media or resized disk sr0
Apr 26 16:00:23 LinuxBox kernel: [86109.956028] VFS: busy inodes on changed media or resized disk sr0
nikbarge@LinuxBox:~$ sudo fdisk -l
[sudo] password for nikbarge: 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051d23

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60144   483106648+  83  Linux
/dev/sdb2           60145       60801     5277352+   5  Extended
/dev/sdb5           60145       60801     5277321   82  Linux swap / Solaris

```

---

### Post by nabarge on 2010-04-27
thought the new updates might help, they didn't. But the logs look different, maybe these will be helpful:

```
nikbarge@LinuxBox:~$ tail /var/log/messages
Apr 27 18:56:30 LinuxBox kernel: [  278.392078] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
Apr 27 18:56:30 LinuxBox kernel: [  278.392085] ata1.01: limiting speed to UDMA/33:PIO3
Apr 27 18:56:30 LinuxBox kernel: [  278.392114] ata1: soft resetting link
Apr 27 18:56:30 LinuxBox kernel: [  278.668023] usb 2-3: new full speed USB device using ohci_hcd and address 8
Apr 27 18:56:30 LinuxBox kernel: [  278.740287] ata1.01: configured for UDMA/33
Apr 27 18:56:35 LinuxBox kernel: [  283.740033] ata1.01: qc timeout (cmd 0xa0)
Apr 27 18:56:35 LinuxBox kernel: [  283.740043] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
Apr 27 18:56:35 LinuxBox kernel: [  283.740048] ata1.01: disabled
Apr 27 18:56:35 LinuxBox kernel: [  283.740087] ata1: soft resetting link
Apr 27 18:56:36 LinuxBox kernel: [  284.064097] ata1: EH complete
nikbarge@LinuxBox:~$ dmesg | tail
[  283.740043] ata1.01: TEST_UNIT_READY failed (err_mask=0x5)
[  283.740048] ata1.01: disabled
[  283.740087] ata1: soft resetting link
[  284.064097] ata1: EH complete
[  290.873777] end_request: I/O error, dev fd0, sector 0
[  290.873787] Buffer I/O error on device fd0, logical block 0
[  303.041243] end_request: I/O error, dev fd0, sector 0
[  303.041253] Buffer I/O error on device fd0, logical block 0
[  315.209423] end_request: I/O error, dev fd0, sector 0
[  315.209433] Buffer I/O error on device fd0, logical block 0

```

---

### Post by nabarge on 2010-04-27
more weirdness.... so just for giggles, I connected this drive to a usb 2.0 hub, and it worked like a charm! So not a real solution, but i'll take a win when i can get one....

---

