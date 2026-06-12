---
title: "Ubuntu 10.04 Reporting Disk Failure (Samsung HD204UI)"
date: 2010-12-21
forum: General Help
---

### Post by rlhorn on 2010-12-21
I have a Samsung HD204UI 2TB HD.
It is partitioned for dual boot as follows:
1TB NTFS Win7 OS
1TB Extended with 760GB Ubuntu 10.04, 16GB Swap and 224gb FAT32

Here is the problem.  Windows is reading the drive/drives as all being "Healthy".  Ubuntu under the "Disk Utility" is stating in the "SMART Status:" [COLOR="Red"]DISK FAILURE IS IMMINENT[/COLOR]. "Self Assessment:" [COLOR="red"]FAILING[/COLOR], and as I look further into it, the "Spinup Time" is what is failing.

I have had this hard drive in the system for maybe a month, and also running both 64 bit Win7 and 64 bit Ubuntu.

Is there another way to check if the disk is actually failing or is this just a report bug in Ubuntu.

Thank you.
Robert

---

### Post by Freak_NL on 2010-12-22
Did you see this:

[http://www.samsung.com/global/business/hdd/faqView.do?b2b_bbs_msg_id=386](http://www.samsung.com/global/business/hdd/faqView.do?b2b_bbs_msg_id=386)   ?

---

### Post by rlhorn on 2010-12-22
I did come across that on Samsung site.  But I guess what is confusing me is windows reports everything is ok i.e. allocation size, # of bytes, etc... the list goes on.  But ubuntu is reporting a disk failure is imminent.
I  read somewhere last night that ubuntu 10.04 does not deal well with a 4096 allocation size, but for the life of me can not find that link again.  Can someone confirm this?  Has ubuntu 10.10 fixed this?  I can not seem to find any info on this for 10.10.
Thanks again,
Robert

---

### Post by piquat on 2010-12-23
> **rlhorn said:**
>  and as I look further into it, the "Spinup Time" is what is failing.

Just to add to this, IF this is the problem, when it starts getting worse, you'll boot the PC and sometimes it'll find that drive and sometimes it won't.  What happens is that it tries to find the drive before it's spun up, if that takes too long it thinks it's not there at all.

If that starts happening then you KNOW it's dying.

---

### Post by rlhorn on 2010-12-23
So far boot ups are fine. (fingers crossed) I am still trying to research it, with very little luck.

---

### Post by Zakhafr on 2010-12-31
Hi,

can you please show use the result of that command on you disk:

```
sudo smartctl -a /dev/sdX
```

*Note:*
- Replace sdX with the appropriate letter for you drive
- If the command do not exist, you should install smartmontools
- The command lists in a text format all the smart parameters of your disk (see: man smartctl)

[I]P.S.: I don't think you can say "Ubuntu doesn't cope well with 4096 byte sectors disks"... In fact those drive report to the O.S. that they have a 512B sectors (512e norm). This is the transitionnal norm, it is meant not to break compatibility with older Windows.
So when you report "I am a drive with 512B sectors" to a Linux kernel, it believes you, and does as if you had a 512B drive!
To correct that, I believe such drives come with an "alignement" tool, but of course it just works for Windows. For Linux you have to "manually" align the partitions when you create them.
Hopefully there will be a documented way to know if it is a real 512B sector disk or a fake 512B, so that O.S. could cope better with that. And ultimately, this is transitionnal. In the future (Advance Format) the disk would advertise their real sector size as 4096 (4Kn norm).
Source: [https://secure.wikimedia.org/wikipedia/en/wiki/Advanced_Format]("https://secure.wikimedia.org/wikipedia/en/wiki/Advanced_Format")
[/I]

---

### Post by rlhorn on 2010-12-31
> P.S.: I don't think you can say "Ubuntu doesn't cope well with 4096 byte sectors disks"...etc...

Please do not take this wrong, I just want to get the quote/facts straight.

I don't think I said "Ubuntu doesn't cope well..", I stated I saw/read somewhere online about the allocation size and was asking for confirmation on if this was true.  As we all know, you can not believe everything you read online.

And thank you for the source link, very interesting.

But anyways, thank you for your response and here are the results:

```

robert@robert-desktop:~$ sudo smartctl -a /dev/sda

[sudo] password for robert: 

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen

Home page is http://smartmontools.sourceforge.net/



=== START OF INFORMATION SECTION ===

Device Model:     SAMSUNG HD204UI

Serial Number:    S2H7JD2ZA10442

Firmware Version: 1AQ10001

User Capacity:    2,000,398,934,016 bytes

Device is:        In smartctl database [for details use: -P show]

ATA Version is:   8

ATA Standard is:  Not recognized. Minor revision code: 0x28

Local Time is:    Fri Dec 31 17:02:09 2010 MST



==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.



SMART support is: Available - device has SMART capability.

SMART support is: Enabled



=== START OF READ SMART DATA SECTION ===

SMART overall-health self-assessment test result: PASSED

See vendor-specific Attribute list for marginal Attributes.



General SMART Values:

Offline data collection status:  (0x00)	Offline data collection activity

					was never started.

					Auto Offline Data Collection: Disabled.

Self-test execution status:      (   0)	The previous self-test routine completed

					without error or no self-test has ever 

					been run.

Total time to complete Offline 

data collection: 		 (20820) seconds.

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

					SCT Feature Control supported.

					SCT Data Table supported.



SMART Attributes Data Structure revision number: 16

Vendor Specific SMART Attributes with Thresholds:

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE

  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0

  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0

  3 Spin_Up_Time            0x0023   067   021   025    Pre-fail  Always   In_the_past 10263

  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       45

  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0

  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0

  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0

  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       219

 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0

 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0

 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       43

181 Unknown_Attribute       0x0022   100   100   000    Old_age   Always       -       1456642

191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       6

192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0

194 Temperature_Celsius     0x0002   064   064   000    Old_age   Always       -       28 (Lifetime Min/Max 15/34)

195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0

196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0

197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0

198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0

199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0

200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       2

223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0

225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       61



SMART Error Log Version: 1

No Errors Logged



SMART Self-test log structure revision number 1

Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error

# 1  Short offline       Completed without error       00%       152         -

# 2  Extended offline    Completed: handling damage??  90%       101         -



SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1

SMART Selective self-test log data structure revision number 0

Warning: ATA Specification requires selective self-test log data structure revision number = 1

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

As of right now, I am running win7 strictly from the Samsung, and have Ubuntu 10.04 on a 500gb WD in a dual boot instead of having them together when all this started.  If one drive goes, at least it is only Win7, so no big loss to me.

But Ubuntu still reports the problem as Win7 does not.

Thank you again for all your help,
Robert

---

### Post by Zakhafr on 2010-12-31
Thanks for your report.

After all we might all be wrong as apparently the disk **IS** in the smartmontools database. This could mean that Ubuntu knows it is a 4096 and act accordingly. This is to be checked and would be a good news. :D

As for the other parameters, appart for one report on spin_up_time, and a strange 2 on Multi_Zone_Error_Rate, your Load_Cycle_Count is very good (low number) for the number of start/stop and hours of power up.

You could try to ask the disk to do an smart auto-test, and check again the parameters.

Sorry, I don't remember how you ask that to the device, you'll have to Google it. :o

And Happy New Year to you all (it's already 2011 here in France)

---

### Post by rlhorn on 2010-12-31
Zakhafr,

Thank you for help.

Oh, and how is the future?  Do we have flying cars yet? :lolflag:

> You could try to ask the disk to do an smart auto-test, and check again the parameters. Yes, I will need to Google this as I do not know myself how to do this.  Do I just Google "smart auto-test" for "Samsung HD204UI HD"? I ask, because I really do not know what I would be looking for.  There is a mention on the Samsung site, [http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html]("http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html") but have no idea if this is what you are speaking of.

I will look further into this in the new year.

Thank you again,
Robert

---

### Post by overlord_tm on 2011-05-22
Did you solve the problem, rlhorn?

Because I have bought 2 brand new HD204UI, put them in raid and got same error 1st day. Now I am wondering, if i should return them into shop and request new ones, or is it just an Ubuntu issue? Running natty.

---

### Post by rlhorn on 2011-06-02
Sorry, haven't been following, just testing.  So far no failure, just the error.  I think it may be an Ubuntu thing (10.04lts 64bit).  Will keep you updated if and when it does fail.

---

### Post by zeta on 2012-02-20
Hi,

I am on my fourth drive by now (on Ubuntu 11.10) and I still get the same error-message. The problem is a bit worse then what you guys are describing - whenever I accidentally go into suspend-to-Ram the drive will not only not wake under Ubuntu. It will also fail to work on Windows (I run in dual-boot). The only way to reactivate the drive is to manually disconnect power. 

Samsung claims there is nothing wrong with their drive, but they exchanged it nevertheless.

---

### Post by alexthunder on 2012-05-02
I have the same problem even in Ubuntu 12.04. 
Sometimes it takes 25 second for my desktop to wake up. When I use Windows, I have no this problem.

```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-24-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F4 EG (AFT)
Device Model:     SAMSUNG HD204UI
Serial Number:    S2H7J9CZB05820
LU WWN Device Id: 5 0024e9 203cf6bdf
Firmware Version: 1AQ10003
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Wed May  2 20:35:51 2012 VOLT

==> WARNING: Using smartmontools or hdparm with this
drive may result in data loss due to a firmware bug.
****** THIS DRIVE MAY OR MAY NOT BE AFFECTED! ******
Buggy and fixed firmware report same version number!
See the following web pages for details:
http://www.samsung.com/global/business/hdd/faqView.do?b2b_bbs_msg_id=386
http://sourceforge.net/apps/trac/smartmontools/wiki/SamsungF4EGBadBlocks

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 137)	The previous self-test completed having
					a test element that failed and the
					device is suspected of having handling
					damage.
Total time to complete Offline 
data collection: 		(19620) seconds.
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
  3 Spin_Up_Time            0x0023   067   021   025    Pre-fail  Always   In_the_past 10014
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2630
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       5377
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2366
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       4793797
191 G-Sense_Error_Rate      0x0022   099   099   000    Old_age   Always       -       16176
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   062   055   000    Old_age   Always       -       38 (Min/Max 16/45)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       13
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       2674

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: handling damage??  90%       245         0

Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed_handling_damage?? [90% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

