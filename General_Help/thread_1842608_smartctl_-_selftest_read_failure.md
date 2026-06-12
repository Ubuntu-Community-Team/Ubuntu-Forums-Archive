---
title: "smartctl - selftest read failure"
date: 2011-09-11
forum: General Help
---

### Post by elysianfields44 on 2011-09-11
Hi all,

Recently while trying to resize one of my partitions, I noticed that gparted displays a "bad sectors on drive" error. So I installed smartmontools and ran the self-test to figure out if there's anything wrong with my hard drive; both self-tests seem to reach a read failure error:

```
:~$ sudo smartctl -l selftest /dev/sda
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: **read failure**       90%      9853         6457807
# 2  Extended offline    Completed: **read failure**       90%      9853         6457807

```

This is the output of smartctl -a /dev/sda:

```
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.4 series
Device Model:     ST9250827AS
Serial Number:    5RG213QW
Firmware Version: 3.AAA
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Sep 11 19:53:27 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: **PASSED**
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
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
recommended polling time: 	 (  92) minutes.
SCT capabilities: 	       (0x0001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3303
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       14
  7 Seek_Error_Rate         0x000f   079   060   030    Pre-fail  Always       -       13196830936
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       9853
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3399
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       383
189 High_Fly_Writes         0x003a   094   094   000    Old_age   Always       -       6
190 Airflow_Temperature_Cel 0x0022   051   037   045    Old_age   Always   In_the_past 49 (0 128 63 16)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       411
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1981
193 Load_Cycle_Count        0x0022   019   019   000    Old_age   Always       -       163591
194 Temperature_Celsius     0x001a   049   063   000    Old_age   Always       -       49 (0 16 0 0)
195 Hardware_ECC_Recovered  0x0012   061   052   000    Old_age   Always       -       43933146
197 Current_Pending_Sector  0x0010   100   100   000    Old_age   Offline      -       1
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       1
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
**ATA Error Count: 384** (device log contains only the most recent five errors)
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

Error 384 occurred at disk power-on lifetime: 9685 hours (403 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cf 89 62 e0  Error: UNC at LBA = 0x006289cf = 6457807

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 cf 89 62 e0 00      01:37:55.842  READ DMA EXT
  ea 00 00 00 00 00 a0 00      01:37:55.842  FLUSH CACHE EXT
  35 00 08 3f 00 5e e0 00      01:37:55.842  WRITE DMA EXT
  35 00 08 07 59 01 e0 00      01:37:55.842  WRITE DMA EXT
  35 00 08 37 58 01 e0 00      01:37:55.821  WRITE DMA EXT

Error 383 occurred at disk power-on lifetime: 9685 hours (403 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cf 89 62 e0  Error: UNC at LBA = 0x006289cf = 6457807

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 bf 89 62 e0 00      01:37:52.711  READ DMA EXT
  35 00 10 df 6f 64 e0 00      01:37:52.733  WRITE DMA EXT
  25 00 10 bf 8c 62 e0 00      01:37:52.733  READ DMA EXT
  35 00 20 df 49 41 e0 00      01:37:52.733  WRITE DMA EXT
  35 00 20 bf 6f 64 e0 00      01:37:52.732  WRITE DMA EXT

Error 382 occurred at disk power-on lifetime: 9523 hours (396 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cf 89 62 e0  Error: UNC at LBA = 0x006289cf = 6457807

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 cf 89 62 e0 00      04:05:11.017  READ DMA EXT
  ea 00 00 00 00 00 a0 00      04:05:11.017  FLUSH CACHE EXT
  35 00 08 3f 00 5e e0 00      04:05:11.017  WRITE DMA EXT
  35 00 08 6f 0c 00 e0 00      04:05:10.991  WRITE DMA EXT
  ea 00 00 00 00 00 a0 00      04:05:10.991  FLUSH CACHE EXT

Error 381 occurred at disk power-on lifetime: 9523 hours (396 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cf 89 62 e0  Error: UNC at LBA = 0x006289cf = 6457807

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 bf 89 62 e0 00      04:05:07.896  READ DMA EXT
  35 00 10 1f da 63 e0 00      04:05:07.895  WRITE DMA EXT
  25 00 10 9f 3a 11 e0 00      04:05:07.895  READ DMA EXT
  35 00 18 07 da 63 e0 00      04:05:07.895  WRITE DMA EXT
  25 00 18 87 3a 11 e0 00      04:05:07.965  READ DMA EXT

Error 380 occurred at disk power-on lifetime: 9507 hours (396 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cf 89 62 e0  Error: UNC at LBA = 0x006289cf = 6457807

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 cf 89 62 e0 00      08:53:36.417  READ DMA EXT
  25 00 08 c7 89 62 e0 00      08:53:36.417  READ DMA EXT
  25 00 08 bf 89 62 e0 00      08:53:36.393  READ DMA EXT
  35 00 38 27 75 96 e0 00      08:53:36.364  WRITE DMA EXT
  35 00 08 b7 74 96 e0 00      08:53:36.364  WRITE DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      9853         6457807
# 2  Extended offline    Completed: read failure       90%      9853         6457807

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


Strangely, you will notice the overall health test result is still PASSED. What could be causing this read failure error, and how could I investigate further what's wrong with the hard drive? 

Also, is there more detailed information on the attributes reported by smartctl and the threshold values?

Thanks in advance.

---

