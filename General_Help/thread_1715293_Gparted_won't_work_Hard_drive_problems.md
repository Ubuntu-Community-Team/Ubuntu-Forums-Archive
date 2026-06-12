---
title: "Gparted won't work: Hard drive problems"
date: 2011-03-26
forum: General Help
---

### Post by s3MA00RRNY on 2011-03-26
A while back I  tried out making a Linux From Scratch system, so I needed an extra  partition. I simply resized my home partition to make room for it. I  don't need the LFS partition anymore, so I deleted it and tried to  resize my home partition again. Gparted  then gives me a bunch of buffer I/O errors and cancels. I checked the  partition for bad blocks and it found some. There were only ten of them  (10K), and they were all in a straight line. If I try to dd them into a  file, and then read the file, the program gets stuck partway through the  read.  I also have 89 ATA errors in my SMART log, but they are not  going up at all. My feeling is that this is just a fluke, but should I  be concerned about this? Here's my log:

```

smartctl 5.40 2010-07-12 r3124 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.4 series
Device Model:     ST9320423AS
Serial Number:    5VH0PRG8
Firmware Version: 0002SDM1
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat Mar 26 21:34:40 2011 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (   0) seconds.
Offline data collection
capabilities:              (0x73) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  78) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   107   097   006    Pre-fail  Always       -       13821560
  3 Spin_Up_Time            0x0003   098   097   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1202
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   065   060   030    Pre-fail  Always       -       81655137857
  9 Power_On_Hours          0x0032   099   093   000    Old_age   Always       -       1746
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   037   020    Old_age   Always       -       1085
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   009   009   000    Old_age   Always       -       91
188 Command_Timeout         0x0032   100   097   000    Old_age   Always       -       197221
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   055   048   045    Old_age   Always       -       45 (Lifetime Min/Max 37/45)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       111
193 Load_Cycle_Count        0x0032   064   064   000    Old_age   Always       -       73955
194 Temperature_Celsius     0x0022   045   052   000    Old_age   Always       -       45 (0 13 0 0)
195 Hardware_ECC_Recovered  0x001a   054   051   000    Old_age   Always       -       13821560
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       3
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       29858612649581
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4251466234
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2923407612
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 89 (device log contains only the most recent five errors)
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

Error 89 occurred at disk power-on lifetime: 1744 hours (72 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cd ee ea 0d

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 c8 ee ea 4d 00      02:08:56.549  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      02:08:56.549  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      02:08:56.540  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      02:08:56.539  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      02:08:56.539  READ NATIVE MAX ADDRESS EXT

Error 88 occurred at disk power-on lifetime: 1744 hours (72 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cd ee ea 0d

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 c8 ee ea 4d 00      02:08:53.728  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      02:08:53.727  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      02:08:53.717  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      02:08:53.622  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      02:08:53.621  READ NATIVE MAX ADDRESS EXT

Error 87 occurred at disk power-on lifetime: 1744 hours (72 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cd ee ea 0d

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 c8 ee ea 4d 00      02:08:50.921  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      02:08:50.920  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      02:08:50.910  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      02:08:50.890  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      02:08:50.889  READ NATIVE MAX ADDRESS EXT

Error 86 occurred at disk power-on lifetime: 1744 hours (72 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cd ee ea 0d

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 c8 ee ea 4d 00      02:08:48.069  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      02:08:48.068  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      02:08:48.060  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      02:08:48.059  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      02:08:48.059  READ NATIVE MAX ADDRESS EXT

Error 85 occurred at disk power-on lifetime: 1744 hours (72 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 cd ee ea 0d

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 c8 ee ea 4d 00      02:08:45.256  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      02:08:45.255  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      02:08:45.247  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      02:08:45.246  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      02:08:45.245  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1745         233500365

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

