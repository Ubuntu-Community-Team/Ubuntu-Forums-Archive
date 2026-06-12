---
title: "Living with back sectors..."
date: 2012-02-09
forum: General Help
---

### Post by n8bounds on 2012-02-09
Set up a new md array yesterday. Saw this as it was finishing, should I be worried or is Linux going to work around the bad sectors from now on? 

[http://pastebin.com/Sj44G83J](http://pastebin.com/Sj44G83J)
```

[ 9496.133195] ata7.00: exception Emask 0x0 SAct 0x1ff SErr 0x0 action 0x0
[ 9496.139360] ata7.00: irq_stat 0x40000008
[ 9496.145989] ata7.00: failed command: READ FPDMA QUEUED
[ 9496.152915] ata7.00: cmd 60/00:10:00:70:39/01:00:15:00:00/40 tag 2 ncq 131072 in
[ 9496.152916]          res 51/40:00:80:70:39/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 9501.150910] ata7.00: status: { DRDY ERR }
[ 9501.163898] ata7.00: error: { UNC }
[ 9501.189295] ata7.00: configured for UDMA/133
[ 9501.189322] ata7: EH complete
[ 9503.647430] ata7.00: exception Emask 0x0 SAct 0x3ff SErr 0x0 action 0x0
[ 9503.660226] ata7.00: irq_stat 0x40000008
[ 9503.673297] ata7.00: failed command: READ FPDMA QUEUED
[ 9503.686285] ata7.00: cmd 60/00:30:00:70:39/01:00:15:00:00/40 tag 6 ncq 131072 in
[ 9503.686287]          res 41/40:00:80:70:39/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 9503.738174] ata7.00: status: { DRDY ERR }
[ 9503.751131] ata7.00: error: { UNC }
[ 9503.776935] ata7.00: configured for UDMA/133
[ 9503.776961] ata7: EH complete
[ 9506.211120] ata7.00: exception Emask 0x0 SAct 0x3ff SErr 0x0 action 0x0
[ 9506.224206] ata7.00: irq_stat 0x40000008
[ 9506.237546] ata7.00: failed command: READ FPDMA QUEUED
[ 9506.250569] ata7.00: cmd 60/00:18:00:70:39/01:00:15:00:00/40 tag 3 ncq 131072 in
[ 9506.250571]          res 41/40:00:80:70:39/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 9506.302435] ata7.00: status: { DRDY ERR }
[ 9506.315383] ata7.00: error: { UNC }
[ 9506.340966] ata7.00: configured for UDMA/133
[ 9506.340991] ata7: EH complete
[ 9508.697465] ata7.00: exception Emask 0x0 SAct 0x3ff SErr 0x0 action 0x0
[ 9508.710465] ata7.00: irq_stat 0x40000008
[ 9508.723706] ata7.00: failed command: READ FPDMA QUEUED
[ 9508.736681] ata7.00: cmd 60/00:30:00:70:39/01:00:15:00:00/40 tag 6 ncq 131072 in
[ 9508.736684]          res 41/40:00:80:70:39/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 9508.788432] ata7.00: status: { DRDY ERR }
[ 9508.801370] ata7.00: error: { UNC }
[ 9508.827105] ata7.00: configured for UDMA/133
[ 9508.827143] sd 6:0:0:0: [sdi] Unhandled sense code
[ 9508.827146] sd 6:0:0:0: [sdi] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9508.827150] sd 6:0:0:0: [sdi] Sense Key : Medium Error [current] [descriptor]
[ 9508.827154] Descriptor sense data with sense descriptors (in hex):
[ 9508.827157]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 9508.827166]         15 39 70 80
[ 9508.827170] sd 6:0:0:0: [sdi] Add. Sense: Unrecovered read error - auto reallocate failed
[ 9508.827175] sd 6:0:0:0: [sdi] CDB: Read(10): 28 00 15 39 70 00 00 01 00 00
[ 9508.827183] end_request: I/O error, dev sdi, sector 356085888
[ 9508.840058] ata7: EH complete
[ 9508.841619] __ratelimit: 3 callbacks suppressed
[ 9508.841623] raid5:md0: read error corrected (8 sectors at 356085888 on sdi)
[ 9508.841717] raid5:md0: read error corrected (8 sectors at 356085896 on sdi)
[ 9508.841721] raid5:md0: read error corrected (8 sectors at 356085904 on sdi)
[ 9509.608970] raid5:md0: read error corrected (8 sectors at 356085912 on sdi)
[ 9509.608976] raid5:md0: read error corrected (8 sectors at 356085920 on sdi)
[ 9509.608980] raid5:md0: read error corrected (8 sectors at 356085928 on sdi)
[ 9509.608983] raid5:md0: read error corrected (8 sectors at 356085936 on sdi)
[ 9509.608986] raid5:md0: read error corrected (8 sectors at 356085944 on sdi)
[ 9509.609092] raid5:md0: read error corrected (8 sectors at 356085952 on sdi)
[ 9509.609096] raid5:md0: read error corrected (8 sectors at 356085960 on sdi)
```

Otherwise, it looks fine:
```

# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdi[3] sdh[2] sdg[1] sde[0]
      976772992 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

I ran badblocks on the offending drive and got nothing:

```


root@ceres:~# badblocks /dev/sdi > badblocks.sdi
root@ceres:~# cat badblocks.sdi 
root@ceres:~# ls -l badblocks.sdi 
-rw-r--r-- 1 root root 0 2012-02-08 19:19 badblocks.sdi

```

---

### Post by iponeverything on 2012-02-09
something strange is going on -- I would double check all the cable connections and use Smartmontools to run diagnostics if it still showing the read errors.

---

### Post by n8bounds on 2012-02-09
Good idea, as you can see I started a long test. In the meant time, here's what she knows so far:

```

# smartctl -a /dev/sdi
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD502HI
Serial Number:    S1VZJDWS456176
Firmware Version: 1AG01118
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Thu Feb  9 09:30:46 2012 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 249)	Self-test routine in progress...
					90% of test remaining.
Total time to complete Offline 
data collection: 		 (6082) seconds.
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
recommended polling time: 	 ( 102) minutes.
Conveyance self-test routine
recommended polling time: 	 (  12) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       25
  3 Spin_Up_Time            0x0007   091   091   011    Pre-fail  Always       -       3780
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       84
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   099   051    Pre-fail  Always       -       10
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       10223
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       23781
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       13
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       83
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       25
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       118
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   076   071   000    Old_age   Always       -       24 (Lifetime Min/Max 17/24)
194 Temperature_Celsius     0x0022   075   070   000    Old_age   Always       -       25 (Lifetime Min/Max 17/29)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       664774758
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 9 (device log contains only the most recent five errors)
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

Error 9 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a7 89 3a e6  Error: UNC at LBA = 0x063a89a7 = 104499623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a6 89 3a e6 08  10d+06:27:03.030  READ DMA
  ca 00 01 b7 a5 00 e0 08  10d+06:27:03.030  WRITE DMA
  ca 00 28 16 a3 1a e7 08  10d+06:27:03.030  WRITE DMA
  ca 00 08 d6 7f 62 e6 08  10d+06:27:03.030  WRITE DMA
  ec 00 00 a7 89 3a a0 08  10d+06:27:03.020  IDENTIFY DEVICE

Error 8 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a7 89 3a e6  Error: UNC at LBA = 0x063a89a7 = 104499623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a6 89 3a e6 08  10d+06:26:59.950  READ DMA
  ca 00 28 e6 e0 4e e7 08  10d+06:26:59.950  WRITE DMA
  ca 00 58 e6 2b 70 e6 08  10d+06:26:59.950  WRITE DMA
  ca 00 68 8e c4 71 e6 08  10d+06:26:59.950  WRITE DMA
  ca 00 30 b6 15 4f e6 08  10d+06:26:59.950  WRITE DMA

Error 7 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a7 89 3a e6  Error: UNC at LBA = 0x063a89a7 = 104499623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a6 89 3a e6 08  10d+06:26:56.780  READ DMA
  ca 00 01 b7 a5 00 e0 08  10d+06:26:56.780  WRITE DMA
  c8 00 01 3f 88 3a e6 08  10d+06:26:56.710  READ DMA
  ec 00 00 a7 89 3a a0 08  10d+06:26:56.710  IDENTIFY DEVICE

Error 6 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a7 89 3a e6  Error: UNC at LBA = 0x063a89a7 = 104499623

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a6 89 3a e6 08  10d+06:26:54.090  READ DMA
  c8 00 01 3f 88 3a e6 08  10d+06:26:54.070  READ DMA
  ca 00 08 8e de 49 e6 08  10d+06:26:54.070  WRITE DMA
  ca 00 28 ee a2 1a e7 08  10d+06:26:54.070  WRITE DMA
  ca 00 01 b7 a5 00 e0 08  10d+06:26:54.070  WRITE DMA

Error 5 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a6 89 3a e6  Error: UNC at LBA = 0x063a89a6 = 104499622

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a6 89 3a e6 08  10d+06:26:51.500  READ DMA
  ca 00 01 b7 a5 00 e0 08  10d+06:26:51.500  WRITE DMA
  c8 00 01 3f 88 3a e6 08  10d+06:26:51.500  READ DMA
  ca 00 48 0e c3 71 e6 08  10d+06:26:51.500  WRITE DMA
  ca 00 28 fe 0b 4f e6 08  10d+06:26:51.500  WRITE DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Self-test routine in progress 90%     23781         -

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

### Post by iponeverything on 2012-02-09
I don't think it is bad blocks. Wait until you get your smart report and google around with more generic parts of errors like: 

"Error: UNC at LBA"

I think that it either a bad controller or a bad drive, I would would put my money on a bad drive.

---

### Post by n8bounds on 2012-02-09
> **iponeverything said:**
> I don't think it is bad blocks. Wait until you get your smart report and google around with more generic parts of errors like: 

"Error: UNC at LBA"

I think that it either a bad controller or a bad drive, I would would put my money on a bad drive.

I hope you're wrong about the controller. It's onboard and holding up four other drives. Probably the drive, like you say.

---

### Post by n8bounds on 2012-02-09
Well, that's odd...

```


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     23783         -


```

---

