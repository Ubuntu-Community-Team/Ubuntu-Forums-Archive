---
title: "Errors on boot up."
date: 2010-02-07
forum: General Help
---

### Post by leona on 2010-02-07
Hi there.

I turned on my computer this morning and have had loads of problems booting up, the system seems to hang, display lots of 'weird' messages which I can make no head or tail of, then eventually it will boot into the gui, I have no idea what is up, how I can fix it, or what.
Don't know if this is relevent but there was an update list night, I think a Kernal update to .27?

Anyway here is what I could drag out the sys.log
```

Feb  7 13:49:53 leona-ubuntu kernel: [  153.665198] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2 frozen
Feb  7 13:49:53 leona-ubuntu kernel: [  153.665260] ata3: SError: { Handshk }
Feb  7 13:49:53 leona-ubuntu kernel: [  153.665309] ata3.00: cmd ca/00:68:7c:94:68/00:00:00:00:00/ef tag 0 dma 53248 out
Feb  7 13:49:53 leona-ubuntu kernel: [  153.665311]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Feb  7 13:49:53 leona-ubuntu kernel: [  153.665367] ata3.00: status: { DRDY }
Feb  7 13:49:53 leona-ubuntu kernel: [  159.010126] ata3: port is slow to respond, please be patient (Status 0xd0)
Feb  7 13:49:53 leona-ubuntu kernel: [  163.707946] ata3: device not ready (errno=-16), forcing hardreset
Feb  7 13:49:53 leona-ubuntu kernel: [  163.707948] ata3: hard resetting link
Feb  7 13:49:53 leona-ubuntu kernel: [  164.183326] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb  7 13:49:53 leona-ubuntu kernel: [  164.490931] ata3.00: NODEV after polling detection
Feb  7 13:49:53 leona-ubuntu kernel: [  164.490933] ata3.00: revalidation failed (errno=-2)
Feb  7 13:49:53 leona-ubuntu kernel: [  164.490981] ata3: failed to recover some devices, retrying in 5 secs
Feb  7 13:49:53 leona-ubuntu kernel: [  111.821464] kjournald starting.  Commit interval 5 seconds
Feb  7 13:49:53 leona-ubuntu kernel: [  111.821476] EXT3-fs: sda8: orphan cleanup on readonly fs
Feb  7 13:49:53 leona-ubuntu kernel: [  111.821482] ext3_orphan_cleanup: deleting unreferenced inode 573496
Feb  7 13:49:53 leona-ubuntu kernel: [  111.821509] ext3_orphan_cleanup: deleting unreferenced inode 573458
Feb  7 13:49:53 leona-ubuntu kernel: [  111.821515] EXT3-fs: sda8: 2 orphan inodes deleted
Feb  7 13:49:53 leona-ubuntu kernel: [  111.821517] EXT3-fs: recovery complete.


```
This rolled around for some time, I also notice that not all of the output from the boot up is logged, lots of things I tried to search for that I saw, are not in the logs, not helpful. :(
Can anyone tell me what's up and how I can fix it?
Thank you in advance,

I'm running Ubuntu 8.04 LTS 64 Bit, if that helps.

A 'worried' Leona. :cry:

---

### Post by leona on 2010-02-09
Hi

I am still getting problems at start up.
I don't see all the errors in the logs but they appear to me that it 'could' be a virtual box issue?  I do have virtual box installed, could it be a mismatch?  I do remember that once when there was a kernal update, Virtual box stopped working, now it gave a command to fix it, but I can't remember what it was, any ideas?

---

### Post by leona on 2010-02-13
Come on guys, please help,  this is still a problem, its not recording all the errors to the log, but it just seems to hang on start up, it takes ages to boot now, over 5 minutes, its silly, someone surely can tell me what is wrong with it.

This is all I can get from the syslog, but there is lots more displayed at the tim, I don't know why it doesn't record it all.
```

Feb 13 10:06:23 leona-ubuntu kernel: [  426.959732] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2 frozen
Feb 13 10:06:23 leona-ubuntu kernel: [  426.959796] ata1: SError: { Handshk }
Feb 13 10:06:23 leona-ubuntu kernel: [  426.959845] ata1.00: cmd ca/00:20:d0:3b:c9/00:00:00:00:00/ec tag 0 dma 16384 out
Feb 13 10:06:23 leona-ubuntu kernel: [  426.959847]          res 40/00:18:c0:dd:c7/00:00:00:00:00/ec Emask 0x4 (timeout)
Feb 13 10:06:23 leona-ubuntu kernel: [  426.959904] ata1.00: status: { DRDY }
Feb 13 10:06:28 leona-ubuntu kernel: [  432.304564] ata1: port is slow to respond, please be patient (Status 0xd0)
Feb 13 10:06:33 leona-ubuntu kernel: [  437.002384] ata1: device not ready (errno=-16), forcing hardreset
Feb 13 10:06:33 leona-ubuntu kernel: [  437.002388] ata1: hard resetting link

```

---

### Post by leona on 2010-03-13
Ok, still no replies do these screen shots help?
Had to take screen shots as these errors didn't seem to appear in any logs and I wasn't about retype it verbatim ! :)

---

### Post by perham on 2010-03-13
it's definitely related to your HDD or its ata connection. check its SMART status. you need to enable SMART from your bios setup, and then you can check your disk's status.

```

sudo apt-get install smartmontools
sudo smartctl -H [yourdisk]


```

put your device name in last command. for example /dev/sda or /dev/sdb etc.

that gives you an idea of how your HDD is doing. you may want to check it thoroughly by the same smartctl. just read its manual (man smartctl). 

if your disks are ok, then please post your motherboard brand and model.

---

### Post by leona on 2010-03-14
Hi.
Firstly, Thank you so much for replying, I've had this problem for weeks now, and didn't know what to do, I assumed it was Hard Drive related, but couldn't confirm it.
I've enabled smpart and ran the commands as you directed.
The results are
```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```
I am running an Asus M2N-E, AMD x2 64 3800+,  Seagate Barracuda ST3250620AS Sata 250Gb H/D.
The All Test Results are 
```

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250620AS
Serial Number:    6QE0BNY0
Firmware Version: 3.AAE
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Mar 14 21:29:47 2010 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       111675624
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1037
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       293933535
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       5129
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1179
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   068   050   045    Old_age   Always       -       538181664
194 Temperature_Celsius     0x0022   032   050   000    Old_age   Always       -       32 (Lifetime Min/Max 0/15)
195 Hardware_ECC_Recovered  0x001a   059   052   000    Old_age   Always       -       6616587
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       18
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```
I see a lot of 'old age' in there, now I don't know if there is refering to its owner! or the drive is old (its a year old!) I'm planning to replace it with the release of 10.04 anyway, hoping it'll last that long!

---

### Post by perham on 2010-03-14
> **leona said:**
> Hi.
Firstly, Thank you so much for replying, I've had this problem for weeks now, and didn't know what to do, I assumed it was Hard Drive related, but couldn't confirm it.
I've enabled smpart and ran the commands as you directed.
The results are
```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```
I am running an Asus M2N-E, AMD x2 64 3800+,  Seagate Barracuda ST3250620AS Sata 250Gb H/D.
The All Test Results are 
```

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250620AS
Serial Number:    6QE0BNY0
Firmware Version: 3.AAE
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Mar 14 21:29:47 2010 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       111675624
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1037
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       293933535
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       5129
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1179
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   068   050   045    Old_age   Always       -       538181664
194 Temperature_Celsius     0x0022   032   050   000    Old_age   Always       -       32 (Lifetime Min/Max 0/15)
195 Hardware_ECC_Recovered  0x001a   059   052   000    Old_age   Always       -       6616587
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       18
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```
I see a lot of 'old age' in there, now I don't know if there is refering to its owner! or the drive is old (its a year old!) I'm planning to replace it with the release of 10.04 anyway, hoping it'll last that long!

SMART seems to be reporting that your HDD is about to be going bad. consider backing up your important data immediately. it may be unrecoverable any minute. other than losing an HDD, I see nothing else wrong there. HDDs are quite cheap these days too. just remember to back up your data periodically and replace the HDD asap. ;)

---

### Post by perham on 2010-03-14
> **perham said:**
> SMART seems to be reporting that your HDD is about to be going bad. consider backing up your important data immediately. it may be unrecoverable any minute. other than losing an HDD, I see nothing else wrong there. HDDs are quite cheap these days too. just remember to back up your data periodically and replace the HDD asap. ;)

on a second note, after a bit of research, it seems that Old_age and Pre_fail errors are quite normal, and your hdd may not be really in danger. although it's good to have a backup in any case. the problem should be from something else. have you tried changing the sata cable and slot?

---

### Post by leona on 2010-04-09
Hi, 
My friend said the same thing to me, he had this trouble and it turned about to be a Bad SATA cable, so I changed it and hey presto it solved the problem, thank you!
Will have to remember that and keep a spare stock of sata cables!.

All sorted now, thank you.

---

### Post by perham on 2010-04-10
> **leona said:**
> Hi, 
My friend said the same thing to me, he had this trouble and it turned about to be a Bad SATA cable, so I changed it and hey presto it solved the problem, thank you!
Will have to remember that and keep a spare stock of sata cables!.

All sorted now, thank you.

great to hear that ;)

---

