---
title: "MDADM RAID 5 failed, but disks are still present"
date: 2010-06-07
forum: General Help
---

### Post by Rizla on 2010-06-07
Hey guys.. I just had a whole 2TB Software RAID 5 blow up on me.  I rebooted my server, which i hardly ever do and low and behold i loose one of my raid 5 sets.  It seems like two of the disks are not showing up properly..  What i mean by that is the OS picks up the disks, but it doesnt see the partitions.

I ran smartct -l on all the drives in question and they're all in good working order.

Is there some sort of repair tool i can use to scan the busted drives (since they're available) to fix any possible errors that might be present.

Here is what the "good" drive looks like when i use sfdisk:
> 
sudo sfdisk -l /dev/sda

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+ 121600  121601- 976760001   83  Linux
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty


Here is what the busted disks look like when I run the same command:
> 
sudo sfdisk -l /dev/sdb

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type
No partitions found


So basically the busted disks have none of the proper partitions.. how can i scan and *HOPEFULLY* fix this.


Thanks for your help, i really apprecaite it.

FYI, this is the smartct output of one of the bad disks that i just listed above:
> 
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDS721010KLA330
Serial Number:    GTA042PBH03NLF
Firmware Version: GKAOAB0A
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Mon Jun  7 20:07:28 2010 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (15354) seconds.
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
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   130   130   054    Pre-fail  Offline      -       150
  3 Spin_Up_Time            0x0007   109   109   024    Pre-fail  Always       -       605 (Average 669)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       21
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   132   132   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       11194
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       21
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       457
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       457
194 Temperature_Celsius     0x0002   166   166   000    Old_age   Always       -       36 (Lifetime Min/Max 19/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

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

### Post by Rizla on 2010-06-08
I take it no one's experienced a two disk failure in a raid 5?  It weird because the disk health is good and they get picked up in BIOS and by the OS..

---

### Post by zabby39103 on 2010-06-27
A 2 disk failure would seem to suggest you're out of luck.  However, the disks aren't totally gone... so theoretically some recovery may be possible - but it would be complex I think and I don't know where to start.

---

