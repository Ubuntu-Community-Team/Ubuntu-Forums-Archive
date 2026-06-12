---
title: "Failing hard disk"
date: 2009-09-03
forum: General Help
---

### Post by verden01 on 2009-09-03
I just installed an alpha version of 9.10 and there's a program on there called disk utility(i think thats what its called). Anyway it says that one of my hard disks is failing (the one with vista on it).I am wondering how accurate this would be?

---

### Post by RedSingularity on 2009-09-03
Look into using a program called GSmartControl to verify it.  Very easy to use.  Comes with a GUI.

---

### Post by DFlame on 2009-09-03
This program reads the SMART attributes from the firmware of your hard disk. SMART is there to monitor the health of a hard disk. There's a variety of attributes that are monitored (hours online, errors encountered, spin up/down times etc).

What has happened is that a certain attribute (or more) has reached a point that the utility considers dangerous. Post up the extended details it gives you if you can, and I can explain further.

Needless to say, I would back up any important information on that hard drive ASAP.

---

### Post by verden01 on 2009-09-03
ok here is the test results

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)



=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (5085) seconds.
Offline data collection
capabilities: 			 (0x79) SMART execute Offline immediate.
					No Auto Offline data collection support.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  67) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   146   143   021    Pre-fail  Always       -       3216
  4 Start_Stop_Count        0x0032   098   098   040    Old_age   Always       -       2428
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       8172
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2225
194 Temperature_Celsius     0x0022   112   253   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       12
200 Multi_Zone_Error_Rate   0x0009   200   155   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       526         -
# 2  Short offline       Completed without error       00%       525         -
# 3  Short offline       Completed without error       00%       524         -

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

### Post by RedSingularity on 2009-09-03
Whats wrong?  It says it passed the tests.

---

### Post by verden01 on 2009-09-03
Yeah i know, DFlame asked me to send the results.

---

### Post by DFlame on 2009-09-03
There's nothing serious wrong with the drive :? The only two entries that I can see that the utility would complain about are these

> 197 Current_Pending_Sector 0x0012 200 200 000 Old_age Always - 1
199 UDMA_CRC_Error_Count 0x000a 200 253 000 Old_age Always - 12

One sector of the disk is due to be remapped, and there's been a few instances where data copied incorrectly. Hardly "failing". The disk has been operating for about a year in total so the above is pretty good considering the age.

With the sense of urgency gone, I still recommend a periodic backup of important data regardless of the condition of the drive.  :)

---

### Post by verden01 on 2009-09-03
DFlame thanks very much for the advice.:D

---

