---
title: "Help parsing long S.M.A.R.T. results"
date: 2011-09-12
forum: General Help
---

### Post by shortridge11 on 2011-09-12
So I have had issues with a folder giving me input/output errors, read that I should test the harddrive to make sure the hardware is ok.  The exact problem I had was that I couldn't look at files in a folder. Using 'ls' in that folder would cause the machine to freeze, and would freeze a terminal.  Other folders on the harddrive were ok, and other partitions on the same harddrive seem ok.  The harddrive is partitioned into 3 partitions, only the one seems to be messed up.  I'm confused about the results because the test says the result of read smart data section says the test passed overall, but the extended test completed with a read failure. I'm hoping there was just some data corruption on that partition and if I reformat it I will be ok.  Thoughts on how to proceed?


running 10.04 LTS


```
xx@xxx:~$ sudo smartctl -a -d ata /dev/sdf
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EARS-00Z5B1
Serial Number:    WD-WMAVU1442372
Firmware Version: 80.00A80
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Sep 12 08:10:00 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 249) Self-test routine in progress...
                                        90% of test remaining.
Total time to complete Offline
data collection:                 (32400) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3031) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   215   181   021    Pre-fail  Always       -       4233
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       256
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       12515
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       250
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       235
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1026401
194 Temperature_Celsius     0x0022   106   093   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       5
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       4

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12502         -
# 2  Extended offline    Completed: read failure       40%     12500         2067728792

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

xx@xxx:~$

```

---

### Post by pqwoerituytrueiwoq on 2011-09-12
boot a live cd and use the disk utility or gparted to check the partition the folder is on

after you get the error can you still access the hdd?

---

### Post by shortridge11 on 2011-09-12
After I get the error I can still access the hdd. I only have ssh access until later tonight, but I think when I get home I'll just end up formatting that partition. I'm just making sure that I'm not going to be destroying the whole hdd if I do that.

---

### Post by pqwoerituytrueiwoq on 2011-09-13
i have no way to know what you will loose without knowing how your partitions are laid  out (gparted screenshot)

---

