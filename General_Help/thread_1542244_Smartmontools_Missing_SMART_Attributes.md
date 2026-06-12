---
title: "Smartmontools Missing SMART Attributes"
date: 2010-07-30
forum: General Help
---

### Post by jason.marshall87 on 2010-07-30
Hi there

I have run Smartmontools under Ubuntu 8.04 (Hardy Heron), using the following commands:

First I perform an extended test:

[FONT=Courier New]smartctl -t long /dev/sda[/FONT]

Then, when the test has completed, I display detailed SMART information:

smartctl -a /dev/sda

***The output is listed below.  As you can see, there seems to be only a subset of SMART attributes.  Specifically, I note that SMART attribute 05 (Reallocated Sectors Count) is not listed.  My understanding is that this is a critical attribute, and accordingly, I cannot understand as to why this should not be displayed.  Could anybody explain as to why it is not?***

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG SSD UM410 Series 2.5" 8GB
Serial Number:
Firmware Version: VAM12D1Q
User Capacity:    8,012,390,400 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Fri Jul 30 13:54:07 2010 BST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 120) seconds.
Offline data collection
capabilities:              (0x53) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      (   2) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       556
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       475
175 Unknown_Attribute       0x0032   100   100   012    Old_age   Always       -       0
176 Unknown_Attribute       0x0032   100   100   012    Old_age   Always       -       0
177 Unknown_Attribute       0x0013   092   092   017    Pre-fail  Always       -       439
178 Unknown_Attribute       0x0013   088   088   012    Pre-fail  Always       -       7
179 Unknown_Attribute       0x0013   099   099   010    Pre-fail  Always       -       8
180 Unknown_Attribute       0x0013   024   024   010    Pre-fail  Always       -       232
181 Unknown_Attribute       0x0032   100   100   010    Old_age   Always       -       0
182 Unknown_Attribute       0x0032   100   100   010    Old_age   Always       -       0
183 Unknown_Attribute       0x0013   100   100   010    Pre-fail  Always       -       0
187 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   253   253   000    Old_age   Always       -       0
232 Unknown_Attribute       0x0013   087   087   012    Pre-fail  Always       -       53
233 Unknown_Attribute       0x0032   092   092   000    Old_age   Always       -       312534788

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       556         -
# 2  Extended offline    Completed without error       00%       554         -
# 3  Extended offline    Completed without error       00%       553         -

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

### Post by dcstar on 2010-07-31
> **jason.marshall87 said:**
> 
........
***The output is listed below.  As you can see, there seems to be only a subset of SMART attributes.  Specifically, I note that SMART attribute 05 (Reallocated Sectors Count) is not listed.  My understanding is that this is a critical attribute, and accordingly, I cannot understand as to why this should not be displayed.  Could anybody explain as to why it is not?***

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     **SAMSUNG SSD** UM410 Series 2.5" 8GB
........

So you want "Reallocated Sectors" on a SSD device that does not reallocate sectors?

---

### Post by jason.marshall87 on 2010-07-31
Hi David
 
Thanks very much for this information.  You say that the Solid State Drive does not reallocate sectors - I had no idea and so that would explain why there is not a corresponding SMART attribute.  However, what happens when there is a bad sector on the drive?  If this is not reallocated, will it simply remain as bad and be flagged-up by, for example, 'badblocks'?
 
Thanks
 
Jason

---

