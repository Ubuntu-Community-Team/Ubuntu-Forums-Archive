---
title: "i/o error, kernel panic, and me"
date: 2010-05-15
forum: General Help
---

### Post by jerome1232 on 2010-05-15
Okay so I posted earlier on a ssh error which turned out to be my little home server dead in the water, had an i/o error on sdb (I wish I could get the actual error but I can't seem to find mention of it my logs). The kernel panic I'm guessing happened while I was rysnc'ing some files to the server (The rsync unexpectedly quite several times then wouldn't work at all)

This thing doesn't do much heavy lifting it just serves as a mumble server (voice) for me and a few friends.

So today I rebooted the server, it came up, ran some checks on the disks, replayed the journal on /dev/voiceserv/Data then booted up all happy like. 

I am now logged into the server via ssh. I ran some smart tests and the drive seems to have passed although I see quite a few errors mentioned.

Should I be concerned about this drive or do you think it was just a hiccup. If it looks like this thing is on it's way out I'd like to just get another disk and migrate any data over to it.

I have a volume that spans across 2 drives, it's partially on the disk in question. It is an expendable data partition, mostly it's just backup's of my media which is also on my main desktop computer.

Here is what smart returns from "sudo smartctl --all /dev/sdb"

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST3160021A
Serial Number:    5JS0GJA4
Firmware Version: 3.04
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sat May 15 13:49:22 2010 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   065   055   006    Pre-fail  Always       -       88463350
  3 Spin_Up_Time            0x0003   097   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       119
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       6
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       499185079
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -       14858
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2172
194 Temperature_Celsius     0x0022   043   072   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x001a   065   055   000    Old_age   Always       -       88463350
197 Current_Pending_Sector  0x0012   076   076   000    Old_age   Always       -       26685
198 Offline_Uncorrectable   0x0010   076   076   000    Old_age   Offline      -       26685
199 UDMA_CRC_Error_Count    0x003e   200   198   000    Old_age   Always       -       8
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   074   227   000    Old_age   Always       -       26

SMART Error Log Version: 1
ATA Error Count: 4311 (device log contains only the most recent five errors)
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

Error 4311 occurred at disk power-on lifetime: 14614 hours (608 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a9 75 dc e0  Error: UNC at LBA = 0x00dc75a9 = 14448041

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 a7 75 dc e0 00      00:01:14.169  READ DMA EXT
  35 03 08 bf 79 f5 e0 00      00:01:14.169  WRITE DMA EXT
  35 03 08 1f 6b f5 e0 00      00:01:22.303  WRITE DMA EXT
  35 03 08 87 1b f5 e0 00      00:01:22.303  WRITE DMA EXT
  35 03 08 67 10 f5 e0 00      00:01:22.302  WRITE DMA EXT

Error 4310 occurred at disk power-on lifetime: 14614 hours (608 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a9 75 dc e0  Error: UNC at LBA = 0x00dc75a9 = 14448041

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 a7 75 dc e0 00      00:01:14.169  READ DMA EXT
  25 03 10 b7 75 dc e0 00      00:01:14.169  READ DMA EXT
  25 03 10 a7 75 dc e0 00      00:01:14.168  READ DMA EXT
  25 03 10 97 75 dc e0 00      00:01:14.168  READ DMA EXT
  25 03 10 87 75 dc e0 00      00:01:14.167  READ DMA EXT

Error 4309 occurred at disk power-on lifetime: 14614 hours (608 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a9 75 dc e0  Error: UNC at LBA = 0x00dc75a9 = 14448041

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 10 a7 75 dc e0 00      00:01:14.169  READ DMA EXT
  25 03 10 97 75 dc e0 00      00:01:14.169  READ DMA EXT
  25 03 10 87 75 dc e0 00      00:01:14.168  READ DMA EXT
  25 03 10 77 75 dc e0 00      00:01:14.168  READ DMA EXT
  25 03 10 67 75 dc e0 00      00:01:14.167  READ DMA EXT

Error 4308 occurred at disk power-on lifetime: 14614 hours (608 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a1 73 dc e0  Error: UNC at LBA = 0x00dc73a1 = 14447521

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 9f 73 dc e0 00      00:00:54.241  READ DMA EXT
  25 03 08 9f 73 dc e0 00      00:00:54.240  READ DMA EXT
  25 03 08 9f 73 dc e0 00      00:01:03.680  READ DMA EXT
  25 03 08 97 73 dc e0 00      00:00:59.717  READ DMA EXT
  25 03 f0 a7 72 dc e0 00      00:00:54.272  READ DMA EXT

Error 4307 occurred at disk power-on lifetime: 14614 hours (608 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a1 73 dc e0  Error: UNC at LBA = 0x00dc73a1 = 14447521

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 9f 73 dc e0 00      00:00:54.241  READ DMA EXT
  25 03 08 9f 73 dc e0 00      00:00:54.240  READ DMA EXT
  25 03 08 97 73 dc e0 00      00:00:54.228  READ DMA EXT
  25 03 f0 a7 72 dc e0 00      00:00:59.717  READ DMA EXT
  25 03 08 9f 72 dc e0 00      00:00:54.272  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     14856         33632097

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

---

### Post by jerome1232 on 2010-05-16
Shameless bump, anybody have some input on the output of smart, is this drive looking like it's getting ready to be replaced?

---

