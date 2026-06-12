---
title: "programs are shutting down all of a sudden"
date: 2009-09-02
forum: General Help
---

### Post by BrownTown6 on 2009-09-02
I have a Dell Optiplex GX260 with UBUNTU 9.04 running on a 80 GB hard drive with 2 GB RAM. I ran a smartmontools check and this is what is came up with.

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar family
Device Model:     WDC WD800BB-75CAA0
Serial Number:    WD-WMA8E3898668
Firmware Version: 16.06V16
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Sep  2 11:59:36 2009 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 249)    Self-test routine in progress...
                    90% of test remaining.
Total time to complete Offline 
data collection:          (3120) seconds.
Offline data collection
capabilities:              (0x3b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  58) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   199   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   104   097   021    Pre-fail  Always       -       3866
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       119
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       8
  7 Seek_Error_Rate         0x000b   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   031   031   000    Old_age   Always       -       50967
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       117
196 Reallocated_Event_Count 0x0032   194   194   000    Old_age   Always       -       6
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 23 (device log contains only the most recent five errors)
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

Error 23 occurred at disk power-on lifetime: 917 hours (38 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 60 d7 f2 00 e0  Error: UNC 96 sectors at LBA = 0x0000f2d7 = 62167

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 60 d7 f2 00 e0 00      00:01:19.850  READ DMA
  c8 00 68 cf f2 00 e0 00      00:01:17.150  READ DMA
  c8 00 68 cf f2 00 e0 00      00:01:14.400  READ DMA
  c8 00 70 c7 f2 00 e0 00      00:01:11.700  READ DMA
  c8 00 78 bf f2 00 e0 00      00:01:09.000  READ DMA

Error 22 occurred at disk power-on lifetime: 917 hours (38 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 68 d7 f2 00 e0  Error: UNC 104 sectors at LBA = 0x0000f2d7 = 62167

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 68 cf f2 00 e0 00      00:01:17.150  READ DMA
  c8 00 68 cf f2 00 e0 00      00:01:14.400  READ DMA
  c8 00 70 c7 f2 00 e0 00      00:01:11.700  READ DMA
  c8 00 78 bf f2 00 e0 00      00:01:09.000  READ DMA
  c8 00 80 b7 f2 00 e0 00      00:01:06.400  READ DMA

Error 21 occurred at disk power-on lifetime: 917 hours (38 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 68 d7 f2 00 e0  Error: AMNF 104 sectors at LBA = 0x0000f2d7 = 62167

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 68 cf f2 00 e0 00      00:01:14.400  READ DMA
  c8 00 70 c7 f2 00 e0 00      00:01:11.700  READ DMA
  c8 00 78 bf f2 00 e0 00      00:01:09.000  READ DMA
  c8 00 80 b7 f2 00 e0 00      00:01:06.400  READ DMA
  c8 00 88 af f2 00 e0 00      00:01:03.900  READ DMA

Error 20 occurred at disk power-on lifetime: 917 hours (38 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 70 d7 f2 00 e0  Error: UNC 112 sectors at LBA = 0x0000f2d7 = 62167

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 70 c7 f2 00 e0 00      00:01:11.700  READ DMA
  c8 00 78 bf f2 00 e0 00      00:01:09.000  READ DMA
  c8 00 80 b7 f2 00 e0 00      00:01:06.400  READ DMA
  c8 00 88 af f2 00 e0 00      00:01:03.900  READ DMA
  c8 00 90 a7 f2 00 e0 00      00:01:01.100  READ DMA

Error 19 occurred at disk power-on lifetime: 917 hours (38 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 78 d7 f2 00 e0  Error: UNC 120 sectors at LBA = 0x0000f2d7 = 62167

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 78 bf f2 00 e0 00      00:01:09.000  READ DMA
  c8 00 80 b7 f2 00 e0 00      00:01:06.400  READ DMA
  c8 00 88 af f2 00 e0 00      00:01:03.900  READ DMA
  c8 00 90 a7 f2 00 e0 00      00:01:01.100  READ DMA
  c8 00 98 9f f2 00 e0 00      00:00:58.300  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -


How big of a problem to i have and how do i fix it?

---

### Post by Vaphell on 2009-09-02
all programs? do they say anything when executed from terminal?
X session crashes (back to the login screen)?

---

### Post by BrownTown6 on 2009-09-03
Yes it is affecting all programs that I know of. It will happen sometime and not happen at other time with the same application. And I still somewhat new to UBUNTU so I down how to run very name programs from the terminal. I usually just wait until I need to use it and then google it.

---

### Post by P4man on 2009-09-03
can check you have enough free diskspace ? run 

```
df -h
```

in a terminal

---

### Post by BrownTown6 on 2009-09-03
This is the disk space results.,

31% of my main disk drive is being used
78% of my external drive
50% of my 4 GB flash drive
1% of my 2 GB flash drive

I was just going to cut and paste but the results where to close to eachother and it wouldn't let me move then.

---

