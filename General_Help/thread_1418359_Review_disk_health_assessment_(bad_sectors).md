---
title: "Review disk health assessment (bad sectors)"
date: 2010-02-28
forum: General Help
---

### Post by Peppep on 2010-02-28
First of all - I am another one of the stupid newbies, however I always do what I can by primary searching to find solutions to problems I'm experiencing. Please bear with me if my questions are stupid.

I am for the first time trying Ubuntu, and immediately got an error message saying "disk has many bad sectors". Windows never gave me any error messages about the disk. After finding [http://ubuntuforums.org/showpost.php?p=6326288&postcount=7](http://ubuntuforums.org/showpost.php?p=6326288&postcount=7), I started a self test myself, and hope that someone is able to review the results and give me a hint in the right direction to be able to repair the HDD.

Before test

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM160HI
Serial Number:    S14QJD0PB17999
Firmware Version: HH100-11
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sun Feb 28 18:07:50 2010 CET

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32)    The self-test routine was interrupted
                    by the host with a hard or soft reset.
Total time to complete Offline 
data collection:          (  59) seconds.
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
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  59) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       10
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2000
  4 Start_Stop_Count        0x0032   083   083   000    Old_age   Always       -       179294
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       10177
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1707
191 G-Sense_Error_Rate      0x0032   002   002   000    Old_age   Always       -       999999
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       76
194 Temperature_Celsius     0x0022   106   046   000    Old_age   Always       -       44 (Lifetime Min/Max 5/64)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       592551
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       8330
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       17182
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     10171         -
# 2  Short offline       Completed without error       00%      8000         -
# 3  Short offline       Completed without error       00%      4677         -
# 4  Short offline       Completed without error       00%      2429         -
# 5  Short offline       Completed without error       00%         1         -
# 6  Short offline       Aborted by host               150%         1         -
# 7  Short offline       Completed without error       00%         0         -
# 8  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```After test

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM160HI
Serial Number:    S14QJD0PB17999
Firmware Version: HH100-11
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sun Feb 28 19:18:03 2010 CET

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection:          (  59) seconds.
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
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  59) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       10
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2000
  4 Start_Stop_Count        0x0032   083   083   000    Old_age   Always       -       179294
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       10178
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1707
191 G-Sense_Error_Rate      0x0032   002   002   000    Old_age   Always       -       999999
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       76
194 Temperature_Celsius     0x0022   124   046   000    Old_age   Always       -       38 (Lifetime Min/Max 5/64)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       592614
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       8330
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       17331
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     10178         -
# 2  Short offline       Completed without error       00%     10171         -
# 3  Short offline       Completed without error       00%      8000         -
# 4  Short offline       Completed without error       00%      4677         -
# 5  Short offline       Completed without error       00%      2429         -
# 6  Short offline       Completed without error       00%         1         -
# 7  Short offline       Aborted by host               150%         1         -
# 8  Short offline       Completed without error       00%         0         -
# 9  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

