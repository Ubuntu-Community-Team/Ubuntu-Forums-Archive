---
title: "Transmission, and external hard disk - weird lockup"
date: 2011-04-04
forum: General Help
---

### Post by night_fox on 2011-04-04
Hellooooooo!

Can anyone help me with this weird problem please?

I'm running Transmission BitTorrent client on ubuntu 10.10 Maverick Meerkat. The files I'm downloading to are on this external HD where lsusb gives me this line:
```
0930:0b09 Toshiba Corp. PX1396E-3T01 External hard drive
```
The file system is Ext3, and it has size 1TB

After a few minutes, Transmission locks up, and something uses up 100% cpu, but it doesn't seem to be a process as such (from top)! I assume its being used by the kernel. dmesg doesn't say anything useful.

Trying to access the external HD in nautilus makes nautilus freeze.

The only way to sort it out is to reboot the HD, i.e power it off then power it back on.

The HD never fails when copying large files to it, or playing a video from it, so whats going on?

:confused:

What could possibly be causing the crashes? Has anyone else had something similar? Does anyone know how to fix it, or if its a bug in the kernel or something?

---

### Post by fela on 2011-04-04
It definitely sounds like a buggy hard drive. I'd backup the data on it to be sure.

Have you checked the SMART data on the drive? Also, what happens when you try to run a fsck?

---

### Post by night_fox on 2011-04-04
Thanks fela,

I ran fsck after the first time this happened, after not fscking it for ages. It fixed a number of errors, but apparently its clean now.

Heres the result of smartctl --all /dev/sdb

```

smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green family
Device Model:     WDC WD10EAVS-00D7B1
Serial Number:    WD-WCAU47723725
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr  5 00:49:44 2011 BST
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
data collection: 		 (23400) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   163   021    Pre-fail  Always       -       6191
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       399
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9290
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       124
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       399
194 Temperature_Celsius     0x0022   115   099   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

```

I've just done smartctl -t long /dev/sdb

It's going to finish at 5am ... Goodnight!

---

### Post by fela on 2011-04-04
Alright, we'll just have to wait :)

---

### Post by night_fox on 2011-04-05
> SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      9294         -


I think the HD's in good condition.

---

### Post by jtarin on 2011-04-05
Is the external drive partitioned? If not I would suggest that you do. I have a 1TB and have it partitioned into 3 partitions and seem not to suffer any ill effects. Your seek and write time to 1TB can be excessive depending on your setup. My external is formatted NTFS as it is also used by my Win7 install. I am constantly writing to it on the average of 12 hrs a day....for the last year.

---

### Post by night_fox on 2011-04-05
Interesting you should say that! No atm its just partitioned into a tiny FAT32 partition for programs that should allow windows (although none of them work) to use the other partition which is Ext3 and takes up nearly all of the disk.

Are you saying that this is a solution to the lockups?

---

### Post by jtarin on 2011-04-06
I'm not saying it's a solution what I am saying this has worked for me. Try downloading your torrent to your onboard disk and see if the problem repeats itself. What torrent client are you using?

---

