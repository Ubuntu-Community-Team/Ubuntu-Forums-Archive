---
title: "Desktop won't boot after shutdown"
date: 2010-10-16
forum: General Help
---

### Post by HLSolbjorg on 2010-10-16
[COLOR="Lime"]*** SOLVED ***
[http://ubuntuforums.org/showthread.php?t=1591382&highlight=Ubuntu+won't+load+anymore](http://ubuntuforums.org/showthread.php?t=1591382&highlight=Ubuntu+won't+load+anymore)[/COLOR]


For the past few days, my Ubuntu server (it is a desktop that functions as a server, Desktop installed) have been very slow.
Today, it stopped responding to ping, I could not SSH into it (once, I managed to come so far that it asked for my password, but I got timed out) and I could not connect via VNC.

I switched it off, to boot it up again. Post completed, and the screen went black, before the white text "Read Error" appeared on the screen.
I shut it down again, waited a minute or so, before switching it back on. This time, the "read error" did not show up. The "text only" startup for Ubuntu showed up, so I hoped it was all okay. It turned out it wasnt.
I have some pictures:
[http://yfrog.com/4pimag0127xj](http://yfrog.com/4pimag0127xj)
[http://yfrog.com/jnimag0128bj](http://yfrog.com/jnimag0128bj)
The top lines are:
```

mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory

```

I tried to boot up using my memory stick with Ubuntu 10.10 on it. It went like it should, but I could not mount my 40 GB file system. "Another operation pending" - I think this is my issue. Altough, I have no idea how to fix it.

fdisk -l: [http://pastebin.com/3xrKu2Fg](http://pastebin.com/3xrKu2Fg)

Any ideas on what could be the issue here, and how to fix it? :)

Thanks in advance,

HLSolbjorg

---

### Post by p12i on 2010-10-16
It's looks like your filesystem is broken. Boot it from live cd and type 
fsck /dev/sda1.

---

### Post by MooPi on 2010-10-16
Possible hard drive failure is all that comes to mind. There are lots of hard disk utility Live CD's and drive specific tools to diagnose hard drive conditions. Ultimate Boot Disk is a good start.
[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by HLSolbjorg on 2010-10-16
> **p12i said:**
> It's looks like your filesystem is broken. Boot it from live cd and type 
fsck /dev/sda1.
I'll try that one. Thanks!

> **MooPi said:**
> Possible hard drive failure is all that comes to mind. There are lots of hard disk utility Live CD's and drive specific tools to diagnose hard drive conditions. Ultimate Boot Disk is a good start.
[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")
I checked with the one in the Ubuntu LiveCD, it came back no errors.
I think that it checked the LiveUSB itself, though, so I'll try the tool you linked and reply! Thanks!

---

### Post by HLSolbjorg on 2010-10-16
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```

Will edit with results from Ultimate Boot tool soon.

---

### Post by HLSolbjorg on 2010-10-16
Sorry for triple-posting, but I'd like you to know that I've updated my thread (new content in THIS post)

```
smartctl 5.39.1 2010-01-28 r3054 [i486-slackware-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST940210AS
Serial Number:    5QX4FJ5C
Firmware Version: 3.ALC
User Capacity:    40,007,761,920 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Oct 16 18:33:11 2010 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (15556) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  55) minutes.
SCT capabilities: 	       (0x0001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       102890986
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       118
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   079   060   030    Pre-fail  Always       -       85977847
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       12140
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       117
187 Reported_Uncorrect      0x0032   098   098   000    Old_age   Always       -       2
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   049   045    Old_age   Always       -       36 (Lifetime Min/Max 36/36)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       97
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       363552
194 Temperature_Celsius     0x0022   036   051   000    Old_age   Always       -       36 (0 17 0 0)
195 Hardware_ECC_Recovered  0x001a   099   061   000    Old_age   Always       -       120623764
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   130   000    Old_age   Always       -       4274
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 4279 (device log contains only the most recent five errors)
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

Error 4279 occurred at disk power-on lifetime: 12139 hours (505 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 1f 13 00 00 e0  Error: ICRC, ABRT 31 sectors at LBA = 0x00000013 = 19

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 20 30 02 00 00 e0 00      00:00:16.234  READ DMA EXT
  25 20 01 01 00 00 e0 00      00:00:16.234  READ DMA EXT
  25 20 01 00 00 00 e0 00      00:00:16.234  READ DMA EXT
  c6 20 10 01 00 00 ef 00      00:00:16.234  SET MULTIPLE MODE
  91 20 3f 01 00 00 ef 00      00:00:11.934  INITIALIZE DEVICE PARAMETERS [OBS-6]

Error 4278 occurred at disk power-on lifetime: 12139 hours (505 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 1f 13 00 00 e0  Error: ICRC, ABRT 31 sectors at LBA = 0x00000013 = 19

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 20 30 02 00 00 e0 00      00:00:18.712  READ DMA EXT
  25 20 01 01 00 00 e0 00      00:00:18.712  READ DMA EXT
  25 20 01 00 00 00 e0 00      00:00:18.712  READ DMA EXT
  c6 20 10 01 00 00 ef 00      00:00:18.712  SET MULTIPLE MODE
  91 20 3f 01 00 00 ef 00      00:00:14.398  INITIALIZE DEVICE PARAMETERS [OBS-6]

Error 4277 occurred at disk power-on lifetime: 12139 hours (505 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 66 03 84 e0  Error: ICRC, ABRT at LBA = 0x00840366 = 8651622

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 5f 03 84 e0 00      04:01:44.840  READ DMA
  27 00 00 00 00 00 e0 00      04:01:44.699  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      04:01:45.898  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 00      04:01:45.898  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      04:01:45.889  READ NATIVE MAX ADDRESS EXT

Error 4276 occurred at disk power-on lifetime: 12139 hours (505 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 66 03 84 e0  Error: ICRC, ABRT at LBA = 0x00840366 = 8651622

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 5f 03 84 e0 00      04:01:44.840  READ DMA
  27 00 00 00 00 00 e0 00      04:01:44.699  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      04:01:44.387  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 00      04:01:43.842  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      04:01:43.842  READ NATIVE MAX ADDRESS EXT

Error 4275 occurred at disk power-on lifetime: 12139 hours (505 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 7f b0 03 84 e0  Error: ICRC, ABRT 127 sectors at LBA = 0x008403b0 = 8651696

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 90 9f 03 84 e0 00      04:01:42.792  READ DMA
  27 00 00 00 00 00 e0 00      04:01:42.784  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      04:01:42.644  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 00      04:01:43.842  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      04:01:43.842  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1

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


EDIT:

This worked for me: [http://ubuntuforums.org/showthread.php?t=1591382&highlight=Ubuntu+won't+load+anymore](http://ubuntuforums.org/showthread.php?t=1591382&highlight=Ubuntu+won't+load+anymore)

---

