---
title: "gparted drive masacre - Help me!"
date: 2011-02-23
forum: General Help
---

### Post by EdgarAllen on 2011-02-23
Hi there!

I *had* a drive with a partition layout like so:
~50gig Windows 7 - NTFS
~100gig Ubuntu - EXT3
~100gig Snow Leopard - HFS+
~100gig Extended Partition
-- ~100gig Swap Disk - exFat 

I wanted to delete the Snow Leopard partition and format the Swap Disk partition to something else. exFat was causing major file size bloat on small files. QT sdk bloated to like 11 gigs or something ridiculous like that.

Anyways, I loaded up an Ubuntu 10.04 LTS live cd and gparted then deleted the Snow Leopard partition. Gparted said "Mission Accomplished" and tried to rescan the drive, but never found it. 

At this point I restarted the computer, a dell laptop, which didn't boot with an unable to find a bootable device error. The ubuntu live cd doesn't see the drive anymore. gparted scans for drives indefinitely and fdisk -l has no output. 

Not really sure how to proceed at this point. Any help or suggestions would be greatly appreciated.

---

### Post by mciverza on 2011-02-23
Since you have already rebooted, I would recommend powering off your computer entirely.
and then re-plugging the drives cables in to check whether wasn't a cable problem that you have experienced.

Is this an internal drive?

---

### Post by EdgarAllen on 2011-02-23
> **mciverza said:**
> Since you have already rebooted, I would recommend powering off your computer entirely.
and then re-plugging the drives cables in to check whether wasn't a cable problem that you have experienced.

Is this an internal drive?

Yes it is an internal drive on a laptop. The bios lists the drive under "Device Info", so it should be connected.

---

### Post by Quackers on 2011-02-23
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by EdgarAllen on 2011-02-23
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```

Identifying MBRs...
no block devices found

```

That's all the output it has given so far. It's still doing whatever it's doing. It has been running for 5-10 minutes, but has not terminated nor given any other output.

---

### Post by Quackers on 2011-02-23
No, that's not good. If you press ctrl+C it should cancel it.
When the terminal prompt is returned please type in ```
sudo fdisk -lu
``` and post the output in your next post within code tags (or type [code] before the text and [ /code] (without the space after [ ) after the text.

---

### Post by EdgarAllen on 2011-02-23
```
sudo fdisk -lu
```
Give no output.

---

### Post by Quackers on 2011-02-23
Hmm, in the absence of further ideas, I suspect that your hard drive may have died. Normally, even if the partition table is damaged you would get some output from either the boot script or fdisk.
All I can suggest is that you wait and see if somebody else can come up with an idea. I'm out of them I'm afraid. Good luck.

---

### Post by EdgarAllen on 2011-02-23
> **Quackers said:**
> Hmm, in the absence of further ideas, I suspect that your hard drive may have died. Normally, even if the partition table is damaged you would get some output from either the boot script or fdisk.
All I can suggest is that you wait and see if somebody else can come up with an idea. I'm out of them I'm afraid. Good luck.

Thanks for the help. It was worth a try.

 

I loaded up knoppix and tried to run testdisk and that was unsuccessful as well.

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.37 (#13 SMP PREEMPT Sun Jan 23 23:54:32 CET 2011)
Compiler: GCC 4.4 - Sep  5 2010 13:29:23
ext2fs lib: 1.41.12, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sr0 - 732 MB / 698 MiB - CHS 357709 1 1 (RO), sector size=2048 - TSSTcorp DVD+-RW TS-T633A


TestDisk exited normally.
```

---

### Post by Quackers on 2011-02-23
I have been lucky and have not had a disc failure (yet!) so I am unsure of the exact symptoms, but yours seem as likely as they could be, unfortunately.

---

### Post by EdgarAllen on 2011-02-23
> **Quackers said:**
> I have been lucky and have not had a disc failure (yet!) so I am unsure of the exact symptoms, but yours seem as likely as they could be, unfortunately.

I've only had one, but it was a gradual failure. Not like this one that just died out of the blue.

---

### Post by Quackers on 2011-02-23
I believe the gradual failure is more common, but I've heard of several that just failed.
However, I may be wrong. Somebody else may come up with an idea yet :-)

---

### Post by EdgarAllen on 2011-02-23
Ok, Small update. I pulled the harddrive out of the laptop and plugged it into to another laptop using an external drive case.

Windows recognized the disk and the partition manager shows it as Unknown uninitialized and completely unallocated.

I'll load up a live cd and give the commands another try and see if they read anything now.

ETA:
The boot script didn't show any output at all and I canceled it after 5 minutes. fdisk -lu still returns no output. This time however, testdisk did find the drive. It's analyzing the drive looking for lost partitions, lets hope that works.

---

### Post by srs5694 on 2011-02-23
I have suggestions for more commands and tools to run. Mostly these are just shots in the dark, in the hope of getting helpful error messages:


[list]
[*]Try running a SMART utility, such as GSmartControl or smartctl, to see if the disk is registering any errors. If the disk has failed completely, a SMART utility may be able to confirm this, and perhaps provide details.
[*]Try running "sudo parted /dev/sda print". This won't fix anything, but it's conceivable it'll produce a more informative error message.
[*]Try installing [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) and running "sudo gdisk -l /dev/sda". Like parted, this won't fix anything, but it might produce a more informative error message.
[/list]

---

### Post by EdgarAllen on 2011-02-23
> **srs5694 said:**
> I have suggestions for more commands and tools to run. Mostly these are just shots in the dark, in the hope of getting helpful error messages:


[list]
[*]Try running a SMART utility, such as GSmartControl or smartctl, to see if the disk is registering any errors. If the disk has failed completely, a SMART utility may be able to confirm this, and perhaps provide details.
[*]Try running "sudo parted /dev/sda print". This won't fix anything, but it's conceivable it'll produce a more informative error message.
[*]Try installing [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) and running "sudo gdisk -l /dev/sda". Like parted, this won't fix anything, but it might produce a more informative error message.
[/list]

I will give those a try if testdisk doesn't work out.

Right now testdisk found two of the partitions, which are the main ones I wish to keep. It can look through the files ok, so there is hope. It also finds a bunch of other partitions that are were previous deletions, or I don't know. One is an EXT4 partition that is the same size and location as the NTFS Windows 7 partition. I am thinking that EXT4 is the partition I had before I installed Windows7. 

It gives me the following error when it finds one of the NTFS partitions
```
Warning: Incorrect number of heads/cylinders 255 (NTFS) != 64 (HD)
Warning: Incorrect number of sectors per track 63 (NTFS) != 32 (HD)
```

From what I've read after a few google searches, I'd have to go into the "Geometry" menu and adjust the settings and rescan, but I am unsure about that. I am still reading up on it. Never used testdisk before. So I expect to break things worse and totally destroy what may be savable on the hard drive.

It's still doing a deep scan and at the current pace, it will be an hour or two before it finishes. At that point, not sure.

ETA:
Finished scanning 
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdc - 320 GB / 298 GiB - CHS 305246 64 32

Warning: the current number of heads per cylinder is 64
but the correct value may be 16.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

```

---

### Post by EdgarAllen on 2011-02-23
Test disk finished scaning and found most of the partitions. They all showed up as deleted except for the last one which was exFAT and set as the boot partition. I corrected the entries, but testdisk can't write the partition table.
```

write_mbr_i386: starting...
file_pread(5,16,buffer,0(0/0/1)) read err: Input/output error

Partition: Read error
Store new MBR code
file_pwrite(5,1,buffer,0(0/0/1)) write err Input/output error
write_all_log_i386: starting...
No extended partition

Partition: Write error
```

So, I guess I need to change the disk geometry. But to what?
When it finished scanning it said:
```
Warning: the current number of heads per cylinder is 64
but the correct value may be 16.
```

But during scanning it mentioned:
```
Warning: Incorrect number of heads/cylinders 255 (NTFS) != 64 (HD)
Warning: Incorrect number of sectors per track 63 (NTFS) != 32 (HD)
```

Should I change the heads to 16 or 255 and the sectors to 63? What happens if I am wrong?

---

### Post by EdgarAllen on 2011-02-23
Still working on it. :(

Anyhoo. I couldn't get testdisk to write the partition table. It would find all the partitions fine, as well as be able to look through the files.

I started to look at other options and I finally got an error messages

sfdisk gives:
```
read: Input/output error

sfdisk: read error on /dev/sda - cannot read sector 0
 /dev/sda: unrecognized partition table type
No partitions found

```

Is there a way to re create the partition table from scratch without effecting anything else?

gdisk finally outputted something. took 20 minutes.
```
sudo gdisk -l /dev/sda
```
```
GPT fdisk (gdisk) version 0.6.14

Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5C14CBBF-A8A5-4933-A160-2AE9CB6C8584
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 625142381 sectors (298.1 GiB)

```

---

### Post by srs5694 on 2011-02-23
"Read error 5" is an input/output error. This is consistent with the "input/output error" and "write error" messages you're getting from TestDisk, and suggests that your disk has failed. Your best option right now is to run a SMART utility. This won't fix things, but it will either confirm the diagnosis of a dead disk or present us with a head-scratcher (if it says the disk is fine).

It looks to me like sector 0, which holds the Master Boot Record (MBR) table, is dead. If so, this will make it impossible to re-create your disk's partitions. I can think of two possible ways around this problem. The first is to re-create your partitions using the GUID Partition Table (GPT) format, which stores its most important data outside of sector 0. This will require you to know the start and end sectors of your partitions. (You can get this information from TestDisk, but IIRC, TestDisk has the annoying habit of translating LBA values to pseudo-CHS values, despite the fact that most tools these days, including GPT, use LBA.) This might or might not work. If it does, you should be able to mount your partition(s) and copy data off of them. The other option is to use [ddrescue](http://www.gnu.org/software/ddrescue/ddrescue.html) or some similar tool to do a low-level copy of the disk to another physical disk. You can then re-create the partition table on the new disk and access the data. This approach is more likely to work, but it will almost certainly be quite time-consuming -- if the disk has lots of bad sectors, ddrescue could end up taking multiple hours or even over a day to copy the disk.

Either way, if the disk is as bad as I think it is, you'll need a new disk. I also recommend you shut down the disk and don't use it *at all* until you're ready to copy the data onto a new disk. The reason is that, if the disk is physically failing, running it could make more sectors fail. Thus, you don't want to run it at all until you're prepared to copy the data off the disk, since trying to do anything else with it runs the risk of making matters worse.

One more point: The disk geometry is irrelevant for most purposes today; it applies only to cylinder/head/sector (CHS) addressing, which maxes out at a bit under 8 GiB. Thus, any disk bigger than this value relies on linear block addressing (LBA) values for its partitions, rather than CHS values. If the partitions' CHS geometries are inconsistent or set strangely, that could confuse some very old utilities or OSes, but for the most part, modern tools ignore CHS values, so you shouldn't worry about it. As noted earlier, TestDisk is a holdout, clinging desperately to the confusing and obsolete CHS values.

---

### Post by EdgarAllen on 2011-02-23
> **srs5694 said:**
> "Read error 5" is an input/output error. This is consistent with the "input/output error" and "write error" messages you're getting from TestDisk, and suggests that your disk has failed. Your best option right now is to run a SMART utility. This won't fix things, but it will either confirm the diagnosis of a dead disk or present us with a head-scratcher (if it says the disk is fine).

It looks to me like sector 0, which holds the Master Boot Record (MBR) table, is dead. If so, this will make it impossible to re-create your disk's partitions. I can think of two possible ways around this problem. The first is to re-create your partitions using the GUID Partition Table (GPT) format, which stores its most important data outside of sector 0. This will require you to know the start and end sectors of your partitions. (You can get this information from TestDisk, but IIRC, TestDisk has the annoying habit of translating LBA values to pseudo-CHS values, despite the fact that most tools these days, including GPT, use LBA.) This might or might not work. If it does, you should be able to mount your partition(s) and copy data off of them. The other option is to use [ddrescue](http://www.gnu.org/software/ddrescue/ddrescue.html) or some similar tool to do a low-level copy of the disk to another physical disk. You can then re-create the partition table on the new disk and access the data. This approach is more likely to work, but it will almost certainly be quite time-consuming -- if the disk has lots of bad sectors, ddrescue could end up taking multiple hours or even over a day to copy the disk.

Either way, if the disk is as bad as I think it is, you'll need a new disk. I also recommend you shut down the disk and don't use it *at all* until you're ready to copy the data onto a new disk. The reason is that, if the disk is physically failing, running it could make more sectors fail. Thus, you don't want to run it at all until you're prepared to copy the data off the disk, since trying to do anything else with it runs the risk of making matters worse.

One more point: The disk geometry is irrelevant for most purposes today; it applies only to cylinder/head/sector (CHS) addressing, which maxes out at a bit under 8 GiB. Thus, any disk bigger than this value relies on linear block addressing (LBA) values for its partitions, rather than CHS values. If the partitions' CHS geometries are inconsistent or set strangely, that could confuse some very old utilities or OSes, but for the most part, modern tools ignore CHS values, so you shouldn't worry about it. As noted earlier, TestDisk is a holdout, clinging desperately to the confusing and obsolete CHS values.

Thank you for the very informative posts. They have been very helpful.

I zeroed out the MBR using dd and now things are starting to pickup the drive and give output.

smartctl output:

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200BEVT-75ZCT1
Serial Number:    WD-WXE508EY2707
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Feb 23 23:03:35 2011 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 112)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (11160) seconds.
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
recommended polling time: 	 ( 131) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always       -       17252
  3 Spin_Up_Time            0x0027   188   186   021    Pre-fail  Always       -       1591
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1048
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   196   194   000    Old_age   Always       -       277
  9 Power_On_Hours          0x0032   074   074   000    Old_age   Always       -       19319
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       640
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       372
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       677216
194 Temperature_Celsius     0x0022   103   097   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       61
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   079   079   000    Old_age   Always       -       15340
241 Unknown_Attribute       0x0032   044   044   000    Old_age   Always       -       156405533404669
242 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       33954318461

SMART Error Log Version: 1
ATA Error Count: 14200 (device log contains only the most recent five errors)
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

Error 14200 occurred at disk power-on lifetime: 19319 hours (804 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 e0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 00 08      01:59:08.318  READ DMA
  ef 10 02 00 00 00 00 08      01:59:08.317  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      01:59:08.317  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      01:59:08.316  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      01:59:08.315  SET FEATURES [Set transfer mode]

Error 14199 occurred at disk power-on lifetime: 19319 hours (804 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 e0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 00 08      01:59:05.354  READ DMA
  ef 10 02 00 00 00 00 08      01:59:05.353  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      01:59:05.353  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      01:59:05.352  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      01:59:05.352  SET FEATURES [Set transfer mode]

Error 14198 occurred at disk power-on lifetime: 19319 hours (804 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 e0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 00 08      01:59:02.260  READ DMA
  ef 10 02 00 00 00 00 08      01:59:02.260  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      01:59:02.259  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      01:59:02.258  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      01:59:02.258  SET FEATURES [Set transfer mode]

Error 14197 occurred at disk power-on lifetime: 19319 hours (804 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 e0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 00 08      01:58:59.159  READ DMA
  ef 10 02 00 00 00 00 08      01:58:59.159  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      01:58:59.159  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      01:58:59.158  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      01:58:59.157  SET FEATURES [Set transfer mode]

Error 14196 occurred at disk power-on lifetime: 19319 hours (804 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 01 00 00 e0  Error: UNC at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 00 08      01:58:56.198  READ DMA
  ef 10 02 00 00 00 00 08      01:58:56.198  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      01:58:56.197  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      01:58:56.196  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      01:58:56.196  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     19306         -
# 2  Short offline       Interrupted (host reset)      80%      6731         -
# 3  Offline             Completed without error       00%         2         -

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

### Post by srs5694 on 2011-02-23
Well, smartctl gave the drive a passing grade, but I'm concerned by a couple of facts in the output: The "raw read error rate" and the "ATA error count." I'm not an expert at interpreting SMART data, though; it could be these issues sound worse than they are. In fact, I just did some digging, and found that Seagate drives, at least, are known to report high "raw read error rate" raw values even when they're fine. Although yours is a Western Digital drive, this alone might not be a serious problem. I've just checked a couple of WD drives of mine, including a WD3200BPVT-00HXZT1 320 GB 2.5-inch drive, and they both report 0 as the raw value for the "raw read error rate," so that hints that your value may be something real. The "ATA error count" is more troubling to me; however, I don't know if this indicates an internal problem or if it could be caused by a bad cable or bad cable connection.

You might want to consider running an active SMART scan using the -t option, as in "smartctl -t short /dev/sda" to perform a quick test (which usually completes in a minute or so) or "smartctl -t long /dev/sda" to perform a more thorough test that's likely to take several minutes. After you do that, use "smartctl -a /dev/sda" again to see the results.

If you're able to write data other than all 0s (such as a normal MBR partition table) to sector 0, you may now be able to recover the partitions. At this point, I'm still suspicious of the drive, although it's conceivable you only had a temporary glitch of some sort, particularly if it's an interface problem caused by a loose cable.

---

### Post by EdgarAllen on 2011-02-24
Could it be something with the onboard sata controller? Earlier when I was running the drive through an USB controller on a different laptop, the speeds were fine, but when I have it installed back in this thing, testdisk was scanning at a rate of one cylinder per minute. It's like everythin was timing out because the read/write speeds were basically zero.

Know what... The motor probably died on the thing. I don't think it's spinning up anymore. Yeah, it's totally dead now. It's getting a read error on every cylinder. Too bad.

Thanks for the help.

---

