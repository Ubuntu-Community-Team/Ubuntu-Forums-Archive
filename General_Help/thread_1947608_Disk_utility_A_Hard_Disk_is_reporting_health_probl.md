---
title: "Disk utility: A Hard Disk is reporting health problems"
date: 2012-03-26
forum: General Help
---

### Post by xtn5021 on 2012-03-26
Here's what I got with smartmontools.

Can anyone explain to me whats going on here?

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.0.0-16-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD2500BEVS-26VAT0
Serial Number:    WD-WXEY08C64604
LU WWN Device Id: 5 0014ee 257a59619
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Mar 26 20:42:52 2012 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 8100) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  96) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       158
  3 Spin_Up_Time            0x0027   185   185   021    Pre-fail  Always       -       1725
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4400
  5 Reallocated_Sector_Ct   0x0033   076   076   140    Pre-fail  Always   FAILING_NOW 990
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4041
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1973
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       168
193 Load_Cycle_Count        0x0032   183   183   000    Old_age   Always       -       53405
194 Temperature_Celsius     0x0022   099   087   000    Old_age   Always       -       48
196 Reallocated_Event_Count 0x0032   191   191   000    Old_age   Always       -       9
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       15
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 311 (device log contains only the most recent five errors)
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

Error 311 occurred at disk power-on lifetime: 4035 hours (168 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9f 87 ff 40  Error: UNC at LBA = 0x00ff879f = 16746399

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 38 60 87 ff 1b 00      01:18:03.007  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:18:03.006  READ LOG EXT
  60 80 30 60 87 ff 1b 00      01:17:59.924  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:59.924  READ LOG EXT
  60 80 28 60 87 ff 1b 00      01:17:56.122  READ FPDMA QUEUED

Error 310 occurred at disk power-on lifetime: 4035 hours (168 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9f 87 ff 40  Error: UNC at LBA = 0x00ff879f = 16746399

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 30 60 87 ff 1b 00      01:17:59.924  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:59.924  READ LOG EXT
  60 80 28 60 87 ff 1b 00      01:17:56.122  READ FPDMA QUEUED
  ef 03 46 00 00 00 00 00      01:17:55.294  SET FEATURES [Set transfer mode]
  c6 00 10 00 00 00 00 00      01:17:55.294  SET MULTIPLE MODE

Error 309 occurred at disk power-on lifetime: 4035 hours (168 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9f 87 ff 40  Error: UNC at LBA = 0x00ff879f = 16746399

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 28 60 87 ff 1b 00      01:17:56.122  READ FPDMA QUEUED
  ef 03 46 00 00 00 00 00      01:17:55.294  SET FEATURES [Set transfer mode]
  c6 00 10 00 00 00 00 00      01:17:55.294  SET MULTIPLE MODE
  60 80 20 60 87 ff 1b 00      01:17:51.897  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:51.897  READ LOG EXT

Error 308 occurred at disk power-on lifetime: 4035 hours (168 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9f 87 ff 40  Error: UNC at LBA = 0x00ff879f = 16746399

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 20 60 87 ff 1b 00      01:17:51.897  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:51.897  READ LOG EXT
  60 80 18 60 87 ff 1b 00      01:17:48.815  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:48.814  READ LOG EXT
  60 80 10 60 87 ff 1b 00      01:17:45.733  READ FPDMA QUEUED

Error 307 occurred at disk power-on lifetime: 4035 hours (168 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9f 87 ff 40  Error: UNC at LBA = 0x00ff879f = 16746399

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 18 60 87 ff 1b 00      01:17:48.815  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:48.814  READ LOG EXT
  60 80 10 60 87 ff 1b 00      01:17:45.733  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:45.732  READ LOG EXT
  60 80 08 60 87 ff 1b 00      01:17:42.650  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

---

### Post by dcstar on 2012-03-27
> **xtn5021 said:**
> Here's what I got with smartmontools.

Can anyone explain to me whats going on here?
...........
Error 307 occurred at disk power-on lifetime: 4035 hours (168 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9f 87 ff 40  **Error: UNC at LBA = 0x00ff879f = 16746399**

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 18 60 87 ff 1b 00      01:17:48.815  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:48.814  READ LOG EXT
  60 80 10 60 87 ff 1b 00      01:17:45.733  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      01:17:45.732  READ LOG EXT
  60 80 08 60 87 ff 1b 00      01:17:42.650  READ FPDMA QUEUED
........

Apart from the continual errors at the **same block** on the disk?

---

### Post by xtn5021 on 2012-03-27
> **dcstar said:**
> Apart from the continual errors at the **same block** on the disk?

I'm sorry.

I'm an ubuntu newbie.

Don't let the join date fool you.

But I am confused on how to fix this?

---

### Post by dcstar on 2012-03-27
> **xtn5021 said:**
> 
.........
But I am confused on how to fix this?

You have a disk going faulty, the "fix" is to replace the disk.

---

### Post by xtn5021 on 2012-03-27
> **dcstar said:**
> You have a disk going faulty, the "fix" is to replace the disk.

Ah ok.

I will buy a new hard drive I suppose.

---

