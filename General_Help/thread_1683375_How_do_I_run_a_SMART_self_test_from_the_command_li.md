---
title: "How do I run a SMART self test from the command line?"
date: 2011-02-07
forum: General Help
---

### Post by w_barnes on 2011-02-07
I need to run a self-test on my external USB drive and don't want to use System -> Disk Utility.

I've taken a look at the man page for udisks and curiously, there does not appear to be an option for self tests.  Is there a way to run a self test using udisks directly from the command line?

Thanks

---

### Post by fabricator4 on 2011-02-07
I don't know about udisk, but you can use badblocks to test a disk:

```

badblocks -p 0 -o out1 -s /dev/sdc1

```

This will do a read-only test and save output to out1 (file)

Use -w for a destructive read/write test (four patterns) which is the best thing to test a drive.

Use -n for a non-destructive read/write test, but it does take longer.

see "man badblocks" for more options.


Chris

---

### Post by w_barnes on 2011-02-07
Thanks Chris, however I'd like to do more than just a scan for bad sectors/blocks on the disk. What I'm looking for is a way to access the SMART data in the hard drive and trigger the drive's internal diagnostics.

I did a little more digging since my first post and found that although there is a programming interface for self tests in udisks it does not appear to be implemented in udisks itself but I could be wrong about that.

So perhaps I need another package like Disk Utility but for the command line. Does any one have any suggestions?

Thanks

---

### Post by fabricator4 on 2011-02-07
Well I don't use it, but it sounds like smartmontools might do what you want.

Chris

---

### Post by w_barnes on 2011-02-07
Thanks Chris. I started looking at smartmontools too and I'm a bit concerned that it may conflict with udisks. I'll give it a shot though and see what happens.

Thanks again for your help

---

### Post by rubylaser on 2011-02-07
This should get you started...
Install smartmontools
```
sudo apt-get install smartmontools
```
Overall-health self-assessment test:
```
smartctl -d ata -H /dev/sdb
```
You can read more data from hard disk by typing following command:
```
smartctl -d ata -a /dev/sdb
```

---

### Post by w_barnes on 2011-02-07
I installed smartmontools and ran "sudo smartctl -i /dev/sdd" and it  returned with "Device does not support SMART" which I know is wrong  because I can get SMART data from Disk Utility for /dev/sdd.

I also tried including -d ata but that tells me /dev/sdd is not an ATA/ATAPI device.

So back to square one, lol.

For now, I'll have to use the GUI based Disk Utility until I find an alternative.

Thanks for your help

---

### Post by psusi on 2011-02-07
Are you sure you are giving it the right drive?

---

### Post by w_barnes on 2011-02-07
yes, that's the correct device file. Here's some output from my messages log file:

```

scsi7 : SCSI emulation for USB Mass Storage devices
scsi 7:0:0:0: Direct-Access     WD       My Book 1110     1032 PQ: 0 ANSI: 4
...
sd 7:0:0:0: Attached scsi generic sg4 type 0
...
sd 7:0:0:0: [sdd] 975400960 512-byte logical blocks: (499 GB/465 GiB)
sd 7:0:0:0: [sdd] Write Protect is off
 sdd: unknown partition table
sd 7:0:0:0: [sdd] Attached SCSI disk

```

As you can see, there is currently no partition. It originally had a NTFS file system which has since been deleted. I'm getting ready to put ext4 on it but would like to do a thorough self test before formatting it because my first attempt to format failed and I'm not sure yet if it was the drive, the cable or the USB port that caused the problem.

---

### Post by psusi on 2011-02-07
That's usb so you need to specify one of the usb options for device type rather than ata.

---

### Post by josh6190 on 2011-02-07
Are you sure a USB can support SMART??? I've not heard of this before. And a quick scroll through a google search seems to back this up. Feel free to correct me if im wrong though, as SMART Tools are not what I would use for flash-drive tests.

---

### Post by rubylaser on 2011-02-07
Exactly right, I should have asked that before.  You could try the Western Digital Data Lifeguard application.  SMART isn't an exact science.  I would fill the volume repeatedly, then write some real data, and md5 checksum it.  And run badblock over the disk too.

---

### Post by psusi on 2011-02-07
> **josh6190 said:**
> Are you sure a USB can support SMART??? I've not heard of this before. And a quick scroll through a google search seems to back this up. Feel free to correct me if im wrong though, as SMART Tools are not what I would use for flash-drive tests.

It is with certain USB to SATA controllers, and we're not talking about a flash-drive.

> **rubylaser said:**
> Exactly right, I should have asked that before.  You could try the Western Digital Data Lifeguard application.  SMART isn't an exact science.  I would fill the volume repeatedly, then write some real data, and md5 checksum it.  And run badblock over the disk too.

Yes, actually, it is an exact science, and it is also what the WD tools use.  Badblocks is depreciated and should not be used these days since it is quite inferior to SMART.  Modern disks have plenty of ECC built in so if there's something wrong, it throws an error; you don't get good reads with incorrect data being returned.

---

### Post by rubylaser on 2011-02-07
My exact science comment came across not how I intended.  Yes, it is a scientific tool, but solely using SMART results as your method of determining a disks longevity and validity, is not a best practice in my opinion.  I always use SMART tests as part of a toolbox of tests to check a disk.

That being said, I'm always willing to learn, and appreciate your insight.  What tools/methods do you use other than SMART to test a disk?

---

### Post by psusi on 2011-02-07
There's none better qualified to determine the health of the drive than the drive itself.  I regularly run the smart selftests and let the smartmon daemon monitor for abnormalities and email me.

---

### Post by w_barnes on 2011-02-08
> **psusi said:**
> That's usb so you need to specify one of the usb options for device type rather than ata.

I checked the man page for smartctl and there is no mention of USB device type. Perhaps I need a different version? I'm currently using version 5.38.

---

