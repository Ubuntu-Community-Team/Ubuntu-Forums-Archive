---
title: "Hard Drive Failing?"
date: 2012-06-27
forum: General Help
---

### Post by ant2ne on 2012-06-27
Twice now my sdc1 has failed with an I/O error. It wouldn't unmount, something about open files. This is my **dmesg | grep sdc**
```
[565878.249364] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[565878.249368] sd 7:0:0:0: [sdc] Sense Key : Aborted Command [current] [descriptor]
[565878.249383] sd 7:0:0:0: [sdc] Add. Sense: No additional sense information
[565878.249387] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 18 ab 97 18 00 01 00 00
[565878.249394] end_request: I/O error, dev sdc, sector 413898520
[565878.249543] Aborting journal on device sdc1-8.
[565878.249568] EXT4-fs error (device sdc1) in ext4_reserve_inode_write: Journal has aborted
[565878.249595] EXT4-fs error (device sdc1) in ext4_reserve_inode_write: Journal has aborted
[565878.249735] EXT4-fs error (device sdc1): ext4_journal_start_sb: Detected aborted journal
[565878.249739] EXT4-fs (sdc1): Remounting filesystem read-only
[565878.249742] EXT4-fs (sdc1): ext4_da_writepages: jbd2_start: 1024 pages, ino 19791891; err -30
[565878.257360] JBD2: I/O error detected when updating journal superblock for sdc1-8.
[565878.316113] sd 7:0:0:0: [sdc] Synchronizing SCSI cache
[565878.316139] sd 7:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[565878.316143] sd 7:0:0:0: [sdc] Stopping disk
[565878.316150] sd 7:0:0:0: [sdc] START_STOP FAILED
[565878.316152] sd 7:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[566019.176372] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[566019.211649] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[566019.211679] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[566019.211698] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[566019.211721] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[566019.211741] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[566069.313404] Buffer I/O error on device sdc1, logical block 88148869
[566069.313408] lost page write due to I/O error on sdc1
[566245.357662] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.376189] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.376215] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382063] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382084] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382105] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382124] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382144] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382162] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382181] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382199] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382218] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.382237] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[566245.997375] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #2 offset 0
[582594.850116] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #12451841 offset 0
[582594.850146] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #29360129 offset 0
[582594.850173] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #16384017 offset 0
[582594.850194] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850201] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850207] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850213] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850219] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850224] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850294] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #15073281 offset 0
[582594.850309] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #11403265 offset 0
[582594.850321] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #2 offset 0
[582594.850335] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #87293953 offset 0
[582594.958480] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #87293953 offset 0
[582795.974625] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #2 offset 0
[622765.164697] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #91357537 offset 0
[622771.042178] EXT4-fs error (device sdc1): ext4_find_entry: reading directory #91357537 offset 0
```
sdc is a critical drive as it hosts my Virtual Box VMs as well as User Data. How do I figure out what is going on and how to keep it up?

---

### Post by Cheesemill on 2012-06-27
> **ant2ne said:**
> Twice now my sdc1 has failed with an I/O error.

Then it's probably on it's way out.

You can check it using tools downloaded from the manufacturers website but personally I would replace it straight away and restore the data it contains from your most recent backup.

If you are getting I/O errors then you have no way of knowing how much of the data is already corrupted.

---

### Post by rubylaser on 2012-06-27
Have you looked at the SMART data for the drive? From the command line...

```
sudo -i
apt-get install smartmontools
smartctl -a /dev/sdc
```

Also, a long test would be a better way to test (wait for it to complete).
```
smartctl -l selftest /dev/sdc
```

Please paste the results back here.  It could be as simple as a bad/loose SATA cable, or a SATA head on the motherboard.   If you're really concerned, back up your data, then write zeroes to the whole disk.  This will remap any bad sectors.  Run a SMART test again after than to view the status of your disk.  Here's how you could do this.  

[COLOR="Red"]**This will overwrite all data on your disk, so ensure you have a good and working backup first before thinking about doing this.  Also, .this will take a long time depending on the size of the disk.**[/COLOR]

```
dd if=/dev/zero of=/dev/sdc bs=1M
```

---

### Post by ant2ne on 2012-07-02
```
vmhost:~# smartctl -a /dev/sdc
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD204UI
Serial Number:    S2H7J1CB805271
Firmware Version: 1AQ10001
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Mon Jul  2 07:34:05 2012 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (20880) seconds.
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
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   093   067   025    Pre-fail  Always       -       2241
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       92
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       7136
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       151
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       117534
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       198
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   061   056   000    Old_age   Always       -       39 (Lifetime Min/Max 17/44)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       441
200 Multi_Zone_Error_Rate   0x002a   001   001   000    Old_age   Always       -       161791
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       151

SMART Error Log Version: 1
ATA Error Count: 26 (device log contains only the most recent five errors)
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

Error 26 occurred at disk power-on lifetime: 3741 hours (155 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec ff 01 01 00 00 a0 00      01:20:47.357  IDENTIFY DEVICE
  a1 ff 01 01 00 00 a0 00      01:20:47.357  IDENTIFY PACKET DEVICE
  00 00 01 01 00 00 00 00      01:20:47.345  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      01:20:47.344  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      01:20:47.344  NOP [Abort queued commands]

Error 25 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.164  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.164  NOP [Abort queued commands]
  ec 00 00 00 00 00 a0 08      01:20:33.159  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.159  NOP [Abort queued commands]
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]

Error 24 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.159  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.159  NOP [Abort queued commands]
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  00 00 40 20 00 00 40 08      01:20:33.153  NOP [Abort queued commands]

Error 23 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  00 00 40 20 00 00 40 08      01:20:33.153  NOP [Abort queued commands]
  60 00 b0 30 0a 00 40 08      01:20:32.204  READ FPDMA QUEUED
  60 00 00 e0 09 00 40 08      01:20:33.153  READ FPDMA QUEUED

Error 22 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.152  NOP [Abort queued commands]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

### Post by rubylaser on 2012-07-02
> **ant2ne said:**
> ```
vmhost:~# smartctl -a /dev/sdc
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD204UI
Serial Number:    S2H7J1CB805271
Firmware Version: 1AQ10001
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Mon Jul  2 07:34:05 2012 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (20880) seconds.
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
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   093   067   025    Pre-fail  Always       -       2241
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       92
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       7136
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       151
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       117534
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       198
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   061   056   000    Old_age   Always       -       39 (Lifetime Min/Max 17/44)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       441
200 Multi_Zone_Error_Rate   0x002a   001   001   000    Old_age   Always       -       161791
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       151

SMART Error Log Version: 1
ATA Error Count: 26 (device log contains only the most recent five errors)
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

Error 26 occurred at disk power-on lifetime: 3741 hours (155 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec ff 01 01 00 00 a0 00      01:20:47.357  IDENTIFY DEVICE
  a1 ff 01 01 00 00 a0 00      01:20:47.357  IDENTIFY PACKET DEVICE
  00 00 01 01 00 00 00 00      01:20:47.345  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      01:20:47.344  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      01:20:47.344  NOP [Abort queued commands]

Error 25 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.164  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.164  NOP [Abort queued commands]
  ec 00 00 00 00 00 a0 08      01:20:33.159  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.159  NOP [Abort queued commands]
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]

Error 24 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.159  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.159  NOP [Abort queued commands]
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  00 00 40 20 00 00 40 08      01:20:33.153  NOP [Abort queued commands]

Error 23 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  00 00 40 20 00 00 40 08      01:20:33.153  NOP [Abort queued commands]
  60 00 b0 30 0a 00 40 08      01:20:32.204  READ FPDMA QUEUED
  60 00 00 e0 09 00 40 08      01:20:33.153  READ FPDMA QUEUED

Error 22 occurred at disk power-on lifetime: 3737 hours (155 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]
  ef 03 45 00 00 00 a0 08      01:20:33.153  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08      01:20:33.153  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:20:33.152  NOP [Abort queued commands]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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


The first thing to do is change your SATA cable.  Your drive looks healthy in that you have no reallocated sectors, or uncorrectable errors.  You do have a large number of UDMA CRC Errors which typically indicates a bad SATA cable.  Try to replace the cable with a new cable.

```
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       **[COLOR="Red"]441[/COLOR]**

```
^ The 441 at the end should say 0. Cyclic redundancy check (CRC) is a method of verifying and correcting data after it is sent. What this warning is telling you is that at one point, data being sent/received by the drive failed this check. The most common cause for this is a faulty cable. Noise or resistence caused a bit to be flipped.

It already occurred so switch cables won't reset the SMART log. You just need to watch for additional errors in the future which could indicate a hard drive / SATA head issue.

---

### Post by Habitual on 2012-07-02
[http://www.bournetoraiseshell.com/article.php/20101112210728775](http://www.bournetoraiseshell.com/article.php/20101112210728775)

---

### Post by ant2ne on 2012-07-04
Thanks for that information. I will swap the cable and continue to observe.

---

### Post by Erik1984 on 2012-07-29
Any follow up on this? Did new SATA cables help? 

I'm getting "READ FPDMA QUEUED" lines in kern.log too. Sometimes the system freezes and I can almost dream what will be in the logs now.  Have this problem with multiple versions of *buntu (lucid, natty and oneiric, so different kernels). Never have issues with the same hard drive in  WIndows and SmartMonTools reports a healthy drive. 

There is a lengthy thread on Launchpad regarding this issue but no definitive solution in there (as this error message can have different causes as it seems): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)

---

### Post by ant2ne on 2012-07-29
I reseated all sata cables and the problem hasn't returned. I also shortly there after reinstalled my os for an unrelated reason. But the problem mayhave been related to loose cables.

---

### Post by sakamoto on 2012-07-29
best way to identify failing hard drives is by listening... you should hear clicking noises. the faster you hear those, the quicker it will be fully broken.

---

### Post by Erik1984 on 2012-07-29
> **ant2ne said:**
> I reseated all sata cables and the problem hasn't returned. I also shortly there after reinstalled my os for an unrelated reason. But the problem mayhave been related to loose cables.

Thanks for replying. By reseating I guess you mean pulling the SATA cables out and connect hem again? Did you put them back in the same ports/slots?

---

