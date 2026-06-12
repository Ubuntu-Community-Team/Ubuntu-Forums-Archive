---
title: "Help with dd if=/dev/zero of=/dev/sda1"
date: 2010-01-08
forum: General Help
---

### Post by argos3016 on 2010-01-08
Hi,
I am in 9.10 LiveCD , low-level formatting an HD  from another computer, but when i did

# dd if=/dev/zero of=/dev/sda1 

dd does something , but at 413 MB stops 

root@ubuntu:~# dd if=/dev/zero of=/dev/sda1
dd: writing to `/dev/sda1': Input/output error
806433+0 records in
806432+0 records out
412893184 bytes (413 MB) copied, 53.0687 s, 7.8 MB/s

I think that the error is produced by a bad sector or similar.
HEEEELP!!!

---

### Post by bodhi.zazen on 2010-01-08
I would agree, it appears you have a hardware problem.

You can test the integrity of the disk :

[http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)

And you can try simply re-formatting, see what happens.

---

### Post by argos3016 on 2010-01-08
> **bodhi.zazen said:**
> I would agree, it appears you have a hardware problem.

You can test the integrity of the disk :

[http://www.captain.at/howto-linux-smartmontools-smartctl.php](http://www.captain.at/howto-linux-smartmontools-smartctl.php)

And you can try simply re-formatting, see what happens.

root@ubuntu:~# dd if=/dev/zero of=/dev/sda1
dd: writing to `/dev/sda1': Input/output error
806433+0 records in
806432+0 records out
412893184 bytes (413 MB) copied, 53.0687 s, 7.8 MB/s

root@ubuntu:~# smartctl -c /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:          ( 426) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  64) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

---

### Post by NoaHall on 2010-01-08
Do you happen to have a USB stick or something plugged in?

If not, sounds like the drive is failing.

---

### Post by argos3016 on 2010-01-08
Well, its a netbook and I have plugged on a DVD external drive with the Ubuntu CD.

---

### Post by NoaHall on 2010-01-08
> **argos3016 said:**
> Well, its a netbook and I have plugged on a DVD external drive with the Ubuntu CD.

Is it a (early) SSD?

---

### Post by argos3016 on 2010-01-08
The netbook has 160GB ATA drive

---

### Post by NoaHall on 2010-01-08
> **argos3016 said:**
> The netbook has 160GB ATA drive

But is it a solid state drive or a hard drive? Solid state drives (in my experience) have had some trouble formatting correctly.

---

### Post by argos3016 on 2010-01-08
No, is a ASUS 1000H with a 160GB hard disk drive.
The most curious thing is nautilus says that HD has 134GB!!!
Maybe is for bad sectors...

---

### Post by argos3016 on 2010-01-09
Ouch!
I remembered last night the hard drive is password locked. Maybe is for that.
See the following link:
[http://www.geckoandfly.com/2009/04/06/unlock-and-recover-hard-drive-password-hard-disk-password-removal-tool/](http://www.geckoandfly.com/2009/04/06/unlock-and-recover-hard-drive-password-hard-disk-password-removal-tool/)

Something like this but for linux?

---

### Post by argos3016 on 2010-01-09
[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

---

### Post by argos3016 on 2010-01-09
hdparm *--security-unlock* PWD?

---

