---
title: "SMART error (CurrentPendingSector) detected on host"
date: 2011-07-25
forum: General Help
---

### Post by Tpolich on 2011-07-25
I just got an email from smartd stating with a subject

SMART error (CurrentPendingSector) detected on host

and it stated 

The following warning/error was logged by the smartd daemon:

Device: /dev/sdb [SAT], 5 Currently unreadable (pending) sectors



I really don't know what this means / what to do. If anyone can help I will really associateship it.


Here is a output of "smart -a /dev/sdb"

```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-2.6.39-ARCH] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K1000.C
Device Model:     Hitachi HDS721010CLA332
Serial Number:    JP2911HD094Z7C
LU WWN Device Id: 5 000cca 373c42a04
Firmware Version: JP4OA3EA
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Jul 25 00:13:53 2011 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                ( 9278) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 155) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   097   097   016    Pre-fail  Always       -       262146
  2 Throughput_Performance  0x0005   137   137   054    Pre-fail  Offline      -       91
  3 Spin_Up_Time            0x0007   154   154   024    Pre-fail  Always       -       264 (Average 228)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       85
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   140   140   020    Pre-fail  Offline      -       30
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       3816
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       85
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       90
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       90
194 Temperature_Celsius     0x0002   166   166   000    Old_age   Always       -       36 (Min/Max 22/43)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       5
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 3
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

Error 3 occurred at disk power-on lifetime: 3773 hours (157 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 55 f6 a4 8e 08  Error: UNC 85 sectors at LBA = 0x088ea4f6 = 143566070

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 4b a4 8e e0 00  15d+05:52:56.645  READ DMA EXT
  27 00 00 00 00 00 e0 00  15d+05:52:56.640  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  15d+05:52:56.516  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00  15d+05:52:56.397  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00  15d+05:52:56.152  READ NATIVE MAX ADDRESS EXT

Error 2 occurred at disk power-on lifetime: 3773 hours (157 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 55 f6 a4 8e 08  Error: UNC 85 sectors at LBA = 0x088ea4f6 = 143566070

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 4b a4 8e e0 00  15d+05:52:37.785  READ DMA EXT
  27 00 00 00 00 00 e0 00  15d+05:52:37.780  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  15d+05:52:37.656  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00  15d+05:52:37.537  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00  15d+05:52:37.291  READ NATIVE MAX ADDRESS EXT

Error 1 occurred at disk power-on lifetime: 3773 hours (157 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 55 f6 a4 8e 08  Error: UNC 85 sectors at LBA = 0x088ea4f6 = 143566070

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 4b a4 8e e8 00  15d+05:52:19.031  READ DMA EXT
  25 00 00 4b a2 8e e8 00  15d+05:52:19.017  READ DMA EXT
  25 00 00 4b a0 8e e8 00  15d+05:52:18.999  READ DMA EXT
  25 00 00 4b 9f 8e e8 00  15d+05:52:18.989  READ DMA EXT
  25 00 00 4b 9d 8e e8 00  15d+05:52:18.979  READ DMA EXT

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

```

---

