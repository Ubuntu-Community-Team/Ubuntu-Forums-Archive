---
title: "get new computer or not?"
date: 2009-09-13
forum: General Help
---

### Post by linuxgrrl on 2009-09-13
My beloved 5 year old Ubuntu system is suddenly acting up very badly.  dmesg is giving errors that the filesystem is trying to write beyond the end of the disk.  My external hard drive (< 6 months old) is mounting "readonly" and throwing errors in dmesg as well. Even trying to backup to a DVD is failing with i/o errors. 

I have no idea what the root of the problem is, but this system has been thru several upgrades of Ubuntu versions without a full reinstall. I think it will take about 15 hours of work to wipe the drives, fully reinstall and get mythtv back up to where it was, etc. (similar amount of time if I bought a new PC). 

Should I waste my time trying to fix this system (otherwise satisfactory), or just buy new?  Also, based on the types of problems, do I need to buy new (internal) hard drives as well?  Currently I have 2 IDE drives inside the machine.  I know there are many test routines I can put them through with knoppix, etc., but they all require one thing I don't have ... gobs of time. 

Based on suddenly everything filesytem-related going bad at once, does that imply that the drives themselves are at fault, or something deeper (drive controllers, etc?)

Just looking for your best guess here so I can cut my losses and start rebuilding my system as quick as possible.

---

### Post by Ms_Angel_D on 2009-09-13
I can't speak for the problems your having, but at 5 years old I say get a new rig, that system has lasted you quite a while. Why not take the opportunity to enjoy some updated stuff.

---

### Post by Topsiho on 2009-09-13
I guess the problem is hardware.
Might be a disk giving up, or the mother board, or else.

If you have not much time you could start testing the memory, using the LiveCD. You could let it run during the night or other hours you are not using the computer.

For testing the hard disk you might hav a look at

[http://ubuntuforums.org/showthread.php?t=59724](http://ubuntuforums.org/showthread.php?t=59724)

Topsiho

---

### Post by rob-ward on 2009-09-13
There could be a number of different problems that could be causing you errors including problems with you hdd's motherboard or memory.

With time you will likely be able to find the problem with the drive but it could take a while.

As far as getting a new hard drive if you get a num computer that would depend on a number of things, mainly how old are the drives?


You could also have a look at the smart output from the drive, you can use the smart tools to do this.

Firstly install smartmontools
```
sudo apt-get install smartmontools 
```then run
```
sudo smartctl -a /dev/sda
```that should give you a printout showing you info about your hdd, post it here if you need help understanding it.

---

### Post by hal8000 on 2009-09-13
I'm still running on 6 year old hardware on a single core P4 2.8GHz and still get an 18 second boot time with Jaunty 9.04 and a little tuning.

What you need is a live linux CD, Jaunty 9.04 can run as a live CD, can't remember if 8.10 does. Alternatives however are knoppix.

Booting from a live CD works even if your hard drives are faulty or not even present on the system.
You need to know what filesystem and partitions you created on your system, chances are you used ext3.

From a jaunty live CD you can type
sudo fdisk -l

to list your partitions, or fdisk -l  (as root) from a knoppix CD.
You can then run a fsck by typing

fsck.ext3 /dev/sda1

on your unmounted partition to see if the disk structure contains errors.
WARNING. You must replace fsck.ext3 with the correct filesystem type
and run it on the correct partition of course. The live CD's are ideal
for this purpose as rescue disks, portable OS's etc.
Hope that helps.

---

### Post by linuxgrrl on 2009-09-13
I ran the memory test and it came back fine. fsck on the / partition came back fine; however the other partitions with media storage were created with xfs.  When I run "xfs_check" on them, they all come back with "bad magic number" and the test won't run further. 

I'm wondering if this traces back to a power outage I had about 2 months ago, my ups device was not connected properly (argh) so the computer had a bad shutdown.

When I rebuild this system (or a new one :) should I continue to use xfs for large file storage, or something else?  I had read on some of the mythtv guides that it was better/faster for deleting large files (like videos of several GB) so that is why I used it.  Now wondering if it is less robust than ext2 or 3?  

thanks.

---

### Post by synapsys on 2009-09-13
I have a couple TB's of videos on an ext3 partition. I have never had any speed or corruption issues.

---

### Post by oboedad55 on 2009-09-13
> **synapsys said:**
> I have a couple TB's of videos on an ext3 partition. I have never had any speed or corruption issues.

+1 ext3

---

### Post by linuxgrrl on 2009-09-14
> **rob-ward said:**
> There could be a number of different problems that could be causing you errors including problems with you hdd's motherboard or memory.

With time you will likely be able to find the problem with the drive but it could take a while.

As far as getting a new hard drive if you get a num computer that would depend on a number of things, mainly how old are the drives?


How old is "old"?  I think I've had this one for about 4 years, doesn't seem so terrible.  Here is my smartctl output though ... what does it mean?

```

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG SP0802N
Serial Number:    S00JJ20X176556
Firmware Version: TK100-24
User Capacity:    33,820,286,976 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Mon Sep 14 20:51:16 2009 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (2880) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  48) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   051    Pre-fail  Always       -       4
  3 Spin_Up_Time            0x0007   076   050   000    Pre-fail  Always       -       4416
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       28
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0024   090   088   000    Old_age   Offline      -       9948
  9 Power_On_Half_Minutes   0x0032   097   097   000    Old_age   Always       -       18231h+54m
 10 Spin_Retry_Count        0x0013   253   253   049    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       17
194 Temperature_Celsius     0x0022   109   109   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x000a   100   100   000    Old_age   Always       -       172546790
196 Reallocated_Event_Count 0x0012   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0033   253   253   010    Pre-fail  Always       -       0
198 Offline_Uncorrectable   0x0031   253   253   010    Pre-fail  Offline      -       0
199 UDMA_CRC_Error_Count    0x000b   100   100   051    Pre-fail  Always       -       0
200 Multi_Zone_Error_Rate   0x000b   100   100   051    Pre-fail  Always       -       0
201 Soft_Read_Error_Rate    0x000b   100   100   051    Pre-fail  Always       -       0

SMART Error Log Version: 1
ATA Error Count: 5
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 5 occurred at disk power-on lifetime: 18231 hours (759 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 4f c2 10  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 da 00 00 4f c2 10 00      00:58:08.938  SMART RETURN STATUS
  ec 00 01 00 00 00 10 00      00:58:08.938  IDENTIFY DEVICE
  ec 00 01 00 00 00 10 00      00:58:08.938  IDENTIFY DEVICE
  c8 00 08 8a cb ca f0 00      00:53:22.000  READ DMA
  c8 00 08 62 cb ca f0 00      00:53:22.000  READ DMA

Error 4 occurred at disk power-on lifetime: 12031 hours (501 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 4f c2 f0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 da 00 00 4f c2 f0 00      05:33:40.688  SMART RETURN STATUS
  ec 00 00 00 00 00 f0 00      05:33:40.625  IDENTIFY DEVICE
  ef 02 00 00 00 00 f0 00      00:00:28.188  SET FEATURES [Enable write cache]
  ec 00 01 00 00 00 b0 00      00:00:28.125  IDENTIFY DEVICE
  c6 00 00 00 00 00 b0 00      00:00:28.125  SET MULTIPLE MODE

Error 3 occurred at disk power-on lifetime: 9640 hours (401 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 4f c2 f0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 da 00 00 4f c2 f0 00   2d+23:45:05.750  SMART RETURN STATUS
  ec 00 00 00 00 00 f0 00   2d+23:45:05.688  IDENTIFY DEVICE
  ef 02 00 00 00 00 f0 00      00:00:36.563  SET FEATURES [Enable write cache]
  ec 00 01 00 00 00 b0 00      00:00:36.500  IDENTIFY DEVICE
  c6 00 00 00 00 00 b0 00      00:00:36.500  SET MULTIPLE MODE

Error 2 occurred at disk power-on lifetime: 8969 hours (373 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 4f c2 f0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 da 00 00 4f c2 f0 00      08:07:51.313  SMART RETURN STATUS
  ec 00 00 00 00 00 f0 00      08:07:51.313  IDENTIFY DEVICE
  ef 02 00 00 00 00 f0 00      00:00:37.438  SET FEATURES [Enable write cache]
  ec 00 01 00 00 00 b0 00      00:00:37.375  IDENTIFY DEVICE
  c6 00 00 00 00 00 b0 00      00:00:37.375  SET MULTIPLE MODE

Error 1 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 01 00 00 a0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b1 c0 00 01 00 00 a0 00      00:00:04.375  DEVICE CONFIGURATION RESTORE
  ef 03 0c 01 00 00 a0 00      00:00:04.375  SET FEATURES [Set transfer mode]
  ec 00 03 01 00 00 a0 00      00:00:04.375  IDENTIFY DEVICE
  91 00 3f 01 00 00 af 00      00:00:04.375  INITIALIZE DEVICE PARAMETERS [OBS-6]
  10 00 00 01 00 00 a0 00      00:00:04.375  RECALIBRATE [OBS-4]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     11999         -
# 2  Extended offline    Completed without error       00%     11999         -
# 3  Short offline       Completed without error       00%     11976         -
# 4  Short offline       Completed without error       00%     11954         -
# 5  Short offline       Completed without error       00%     11931         -
# 6  Short offline       Completed without error       00%     11916         -
# 7  Extended offline    Completed without error       00%     11916         -
# 8  Short offline       Completed without error       00%     11893         -
# 9  Short offline       Completed without error       00%     11871         -
#10  Short offline       Completed without error       00%     11848         -
#11  Short offline       Completed without error       00%     11826         -
#12  Short offline       Completed without error       00%     11803         -
#13  Short offline       Completed without error       00%     11781         -
#14  Short offline       Completed without error       00%     11758         -
#15  Extended offline    Completed without error       00%     11758         -
#16  Short offline       Completed without error       00%     11735         -
#17  Short offline       Completed without error       00%     11713         -
#18  Short offline       Completed without error       00%     11690         -
#19  Short offline       Completed without error       00%     11668         -
#20  Short offline       Completed without error       00%     11645         -
#21  Short offline       Completed without error       00%     11623         -

Device does not support Selective Self Tests/Logging

```

---

### Post by DasEi on 2009-09-15
smart can either be enabled in bios-setup,  or via sudo smartctl, the man smartctl tells you how to enable it, otherwise for your hd's its a good idea to have e2fsck check them, that won't take ages

---

