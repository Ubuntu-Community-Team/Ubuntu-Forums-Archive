---
title: "ata1.01: status: {DRDY ERR}"
date: 2009-08-28
forum: General Help
---

### Post by rootless on 2009-08-28
Hey, Ubuntu works fine until I startx, at which point, my desktop launches, but my system monitor reads 100% processor usage. If I click on anything, the system becomes unresponsive. When I start gnome, if I go back down to the cli, I can see the following errors being thrown.

```
[various changing numbers] ata1.01: status: {DRDY ERR}
[various changing numbers] ata1.01 ERROR: {unc}
[various changing numbers] ata1.01 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[various changing numbers] ata1.01 cmd c8/00:08:5f:99:e5/00:00:00:00:00/f0 tag 0 dma 4069 in

```

Can anyone help me with this? Any advice at all would be good, even if it's not a solution.

---

### Post by CatKiller on 2009-08-28
I believe that * ERROR: {unc}* means "Uncorrectable Data." Sounds like the hard drive could be on the way out. The manufacturer of the hard drive may have a diagnostic tool on their website, and it may help, but backup all the data that you can. Now.

---

### Post by rootless on 2009-08-29
That's too bad... It's a new drive though.

Do you think a drive could be behind these problems? it's such a weird problem- it only happens when X is running, and this %100 processor thing...

You really think it's a drive?

---

### Post by CatKiller on 2009-08-29
While you're wondering about it, you could be backing up your data. It's a new drive, so it won't take long.

I think it *could* be the drive failing, which is why you have to take every precaution. You don't want to lose any more of your data than you have to. The manufacturer's diagnostic may tell you more. They won't give you a replacement drive until you've run it, anyway.

It might be something entirely benign, but do you really want to take the risk?

I had a similar message on two brand new drives (but without the {unc}, which should worry you) but when I lowered the processor clock all was fine. There might be something similarly non drive-related causing your problem.

---

### Post by msrk on 2009-09-15
I got the same error and read some forums.  I installed smartmontools and ran some commands.  Following is a transcript of the session.  I don't understand the output.  Is there a hardware problem with my disk or is something configured wrong?  Any help would be appreciated.  Thank you, Marc


Session Transcript:

 root@ny:~# smartctl -a -d ata -s on /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar RE EIDE family
Device Model:     WDC WD3200SB-01KMA0
Serial Number:    WD-WCAMR3541958
Firmware Version: 08.05J08
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Sep 15 07:55:31 2009 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

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
data collection: 		 (9600) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 116) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.
SCT capabilities: 	       (0x001f)	SCT Status supported.
					SCT Feature Control supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   226   182   021    Pre-fail  Always       -       3691
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   067   067   000    Old_age   Always       -       24383
 10 Spin_Retry_Count        0x0013   100   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       54
194 Temperature_Celsius     0x0022   113   098   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   186   186   000    Old_age   Always       -       773
198 Offline_Uncorrectable   0x0010   186   186   000    Old_age   Offline      -       773
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   197   197   051    Pre-fail  Offline      -       166

SMART Error Log Version: 1
Warning: ATA error count 45602 inconsistent with error log pointer 3

ATA Error Count: 45602 (device log contains only the most recent five errors)
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

Error 45602 occurred at disk power-on lifetime: 24383 hours (1015 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ce ae c2 f6  Error: UNC 1 sectors at LBA = 0x06c2aece = 113422030

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 ae c2 06 59  33d+17:23:45.980  READ DMA
  27 00 00 00 00 00 00 59  33d+17:23:45.980  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 59  33d+17:23:45.975  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 59  33d+17:23:45.965  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 59  33d+17:23:45.950  READ NATIVE MAX ADDRESS EXT

Error 45601 occurred at disk power-on lifetime: 24383 hours (1015 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ce ae c2 f6  Error: UNC 1 sectors at LBA = 0x06c2aece = 113422030

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 ae c2 06 59  33d+17:23:43.980  READ DMA
  27 00 00 00 00 00 00 59  33d+17:23:43.980  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 59  33d+17:23:43.970  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 59  33d+17:23:43.965  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 59  33d+17:23:43.950  READ NATIVE MAX ADDRESS EXT

Error 45600 occurred at disk power-on lifetime: 24383 hours (1015 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ce ae c2 f6  Error: UNC 1 sectors at LBA = 0x06c2aece = 113422030

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 ae c2 06 59  33d+17:23:41.985  READ DMA
  27 00 00 00 00 00 00 59  33d+17:23:41.985  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 59  33d+17:23:41.975  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 59  33d+17:23:41.965  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 59  33d+17:23:41.950  READ NATIVE MAX ADDRESS EXT

Error 45599 occurred at disk power-on lifetime: 24383 hours (1015 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ce ae c2 f6  Error: UNC 1 sectors at LBA = 0x06c2aece = 113422030

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 ae c2 06 59  33d+17:23:39.815  READ DMA
  27 00 00 00 00 00 00 59  33d+17:23:39.815  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 59  33d+17:23:39.805  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 59  33d+17:23:39.805  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 59  33d+17:23:39.790  READ NATIVE MAX ADDRESS EXT

Error 45598 occurred at disk power-on lifetime: 24383 hours (1015 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ce ae c2 f6  Error: UNC 1 sectors at LBA = 0x06c2aece = 113422030

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c7 ae c2 06 59  33d+17:23:37.495  READ DMA
  27 00 00 00 00 00 00 59  33d+17:23:37.490  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 59  33d+17:23:37.485  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 59  33d+17:23:37.485  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 59  33d+17:23:37.470  READ NATIVE MAX ADDRESS EXT

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

root@ny:~#

---

### Post by danwood76 on 2009-09-15
> ATA Error Count: 45602 (device log contains only the most recent five errors)

Drive is pretty screwed backup and if the drive is new RMA it.
45000 errors is a hell of a lot and signifies a pretty dead drive.

---

### Post by Kuea on 2009-09-15
I was having the same issue a few weeks ago.  Similar errors would fill the logs and the system would lock up - but only under heavy usage.  Booting up to X was fine, and everything else was fine until any heavy usage.

I swapped drives, and to my amazement i had the same problem with a known good drive!

It turned out to be a failing-but-not-quite-dead-yet power supply.  My guess is that when the cpu was at 100% and disk activity going on there wasn't enough power for everything and the hard drives would reset, or have some sort of issue.

Not enough to have the system reset but just enough to be a big problem.  New replacement power supply and everything is fine.

So - it may be the drive, it may not be.  You'll need to do more testing.  Have any spare drives you can perhaps mirror and test?

---

### Post by Zeerots on 2009-09-17
Two days ago after an update on my two 9.04 main PCs I got the same problem on 2 PCs ! I believe it has something to do with a bug in combination with certain chips. See also the big problems with version 9.10 alpha 5:

---

### Post by danwood76 on 2009-09-17
That maybe but the smart errors dont lie and that drive looks like its failing.

---

### Post by tvtech on 2009-09-18
**bold font. I had this same error, I searched and searched and searched. the only common link I found in ALL of them was firefox 3.5  I have had two major kernel panics after installing and while running 3.5  the second one cause the error you described. it took 20 minutes to reboot I have reverted to firefox 3.0 and to err on the side of caution will use opera instead.has anyone filed a bug report?**

---

### Post by jazzgossen on 2010-02-03
I'm running 9.10 and have similar problems too. I use Opera and not Firefox (though I have it installed). I don't think it's Firefox's fault. I also have SMART tests failing, so I'll call HP for a replacement HDD (it's less than a year old).

---

### Post by tvtech on 2010-02-05
This turned into a total HDD failure for me.  I RMA'd that bugger to Asus and all was well.  It took a while to get it to fail in vista which was required by ASUS before they would RMA.  But once I reformatted it, the initial boot gave me a fantastic Bsod and a log failure file in windows and Asus was more than happy to give me a new HDD.

What precipitated this failure was a heavy read write cycle while running unbuntu 9.04 and Windows in virtual box.  I was running several fairly intensive applications in virtual box, and only running firefox in Ubuntu.  The virtual machine was being run off a separate HDD that did not fail when the system crashed.  Firefox crashed in ubuntu and brought down the rest of the system with it, oddly my virtual box was relatively unaffected but ubuntu was totally unresponsive.  The heavy read write and sudden stop appears to have been what damaged the HDD.  I'm not blaming anyone because I got a RMA but beware of this.  I've seen a lot of other reports of Ubuntu eating HDD's for lunch!

---

