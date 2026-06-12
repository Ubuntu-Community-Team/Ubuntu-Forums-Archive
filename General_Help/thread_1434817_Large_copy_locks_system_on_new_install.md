---
title: "Large copy locks system on new install"
date: 2010-03-20
forum: General Help
---

### Post by BiggerGeek on 2010-03-20
Hello,

Here's the deal. I just did a fresh install on my system. The machine has 4 GB of ram, running a 2.66 GHz Core 2 Quad.

I have 5 hard drives in the machine, 4 of which have 500 GB raid 5 partitions with lvm on top. On that raid 5, I have a root partition (ext4), 4 GB swap, a home partition and the bulk of the drives is an XFS data partition.

The other drive, I just have a bunch of backup data on, that I want to move onto the XFS partition.

Whenever I put files copying, the computer literally becomes unusable, and the copy speeds are literally 3-5 MB/s. The system isn't completely hung up, but it is like you move the mouse, and 3 seconds later it moves on the screen. You click a button the cancel the move, and it takes about a minute before things go back to normal.

I did smartctl checks on all the drives, and my sdc has some errors. I Would like to take it out and use the 5th drive to replace is, but i need to get the data off of it first so I can reformat. In my syslog, I am getting a bunch of messages like this:
```

Call Trace:
[  720.870085]  [<ffffffffa016efb0>] ? xfs_sync_inode_data+0x0/0xe0 [xfs]
[  720.870099]  [<ffffffffa0163495>] xfs_ioend_wait+0x85/0xc0 [xfs]
[  720.870104]  [<ffffffff81078a30>] ? autoremove_wake_function+0x0/0x40
[  720.870117]  [<ffffffffa016f088>] xfs_sync_inode_data+0xd8/0xe0 [xfs]
[  720.870130]  [<ffffffffa016f1d2>] xfs_inode_ag_walk+0x72/0xd0 [xfs]
[  720.870142]  [<ffffffffa016efb0>] ? xfs_sync_inode_data+0x0/0xe0 [xfs]
[  720.870155]  [<ffffffffa016f297>] xfs_inode_ag_iterator+0x67/0xa0 [xfs]
[  720.870168]  [<ffffffffa016f4e9>] xfs_sync_data+0x29/0x60 [xfs]
[  720.870180]  [<ffffffffa016f5a3>] xfs_quiesce_data+0x33/0x70 [xfs]
[  720.870193]  [<ffffffffa016c690>] xfs_fs_sync_super+0x70/0x100 [xfs]
[  720.870197]  [<ffffffff8114005e>] ? sync_inodes_sb+0x9e/0xb0
[  720.870200]  [<ffffffff81143e45>] __sync_filesystem+0x45/0x70
[  720.870202]  [<ffffffff81143f37>] sync_filesystems+0xc7/0x120
[  720.870205]  [<ffffffff81143fec>] sys_sync+0x1c/0x40
[  720.870208]  [<ffffffff81012082>] system_call_fastpath+0x16/0x1b
[  840.870047] INFO: task sync:5345 blocked for more than 120 seconds.
[  840.870050] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.870052] sync          D 0000000000000000     0  5345   5340 0x00000000
[  840.870055]  ffff880059931d18 0000000000000086 0000000000000600 0000000000015880
[  840.870059]  ffff880079163110 0000000000015880 0000000000015880 0000000000015880
[  840.870062]  0000000000015880 ffff880079163110 0000000000015880 0000000000015880
```

here is the output of smartctl -a:

```

sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD5000AAJS-00YFA0
Serial Number:    WD-WCAS81512845
Firmware Version: 12.01C02
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Mar 20 17:57:32 2010 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 113)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (13200) seconds.
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
recommended polling time: 	 ( 154) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       146
  3 Spin_Up_Time            0x0003   200   179   021    Pre-fail  Always       -       4958
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       351
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18852
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       347
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       338
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       371
194 Temperature_Celsius     0x0022   111   092   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       35
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 1152 (device log contains only the most recent five errors)
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

Error 1152 occurred at disk power-on lifetime: 18830 hours (784 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3c 41 02 e0  Error: UNC at LBA = 0x0002413c = 147772

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3c 41 02 3a 08   1d+00:17:07.736  READ DMA EXT
  27 00 00 00 00 00 00 08   1d+00:17:07.698  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   1d+00:17:07.678  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08   1d+00:17:07.660  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   1d+00:17:07.660  READ NATIVE MAX ADDRESS EXT

Error 1151 occurred at disk power-on lifetime: 18830 hours (784 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3c 41 02 e0  Error: UNC at LBA = 0x0002413c = 147772

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3c 41 02 3a 08   1d+00:17:04.688  READ DMA EXT
  27 00 00 00 00 00 00 08   1d+00:17:04.618  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   1d+00:17:04.598  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08   1d+00:17:04.581  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   1d+00:17:04.581  READ NATIVE MAX ADDRESS EXT

Error 1150 occurred at disk power-on lifetime: 18830 hours (784 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3c 41 02 e0  Error: UNC at LBA = 0x0002413c = 147772

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3c 41 02 3a 08   1d+00:17:01.476  READ DMA EXT
  27 00 00 00 00 00 00 08   1d+00:17:01.431  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   1d+00:17:01.411  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08   1d+00:17:01.393  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   1d+00:17:01.393  READ NATIVE MAX ADDRESS EXT

Error 1149 occurred at disk power-on lifetime: 18830 hours (784 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3c 41 02 e0  Error: UNC at LBA = 0x0002413c = 147772

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3c 41 02 3a 08   1d+00:16:58.475  READ DMA EXT
  27 00 00 00 00 00 00 08   1d+00:16:58.434  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   1d+00:16:58.414  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08   1d+00:16:58.399  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   1d+00:16:58.399  READ NATIVE MAX ADDRESS EXT

Error 1148 occurred at disk power-on lifetime: 18830 hours (784 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3c 41 02 e0  Error: UNC at LBA = 0x0002413c = 147772

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3c 41 02 3a 08   1d+00:16:55.249  READ DMA EXT
  27 00 00 00 00 00 00 08   1d+00:16:55.208  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08   1d+00:16:55.192  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08   1d+00:16:55.192  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08   1d+00:16:55.192  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       10%     18833         867501579

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

Also, I dont know if it is related in any way, but at boot, I am getting a grub error "error reading biosdisk" or something of the sort.

Also note, i get the same issue whether I cam copying to the XFS partition or an ext4 one

Question if, is it reasonable to think my sdc is causing all the problems? If I remove it and work with a degraded array, will the performance still be bad (can I remove it, copy the data to the degraded array and then run a destructive test on it or replace it with my backup drive).

Any help would be appreciated

---

### Post by BiggerGeek on 2010-03-20
nevermind all. I removed the disk from the array and all works fine..

---

