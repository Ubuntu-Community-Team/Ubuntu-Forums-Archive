---
title: "How can I Detect Failed Hardware?"
date: 2006-06-22
forum: General Help
---

### Post by ssalman on 2006-06-22
This is not necessarily an Ubuntu question! But it is a linux/hardware question.

I'm currently trying to fix a desktop, it had WinXP and it could not boot because of a constant BlueScreenOfDeath at startup. I formatted the HD and ran chkdsk, which found few bad sectors, and then I installed a brand new WinXP on it, but it only took a month to go back to the constant BSOD.

I'm suspecting a bad HD, but I'm not sure. I tested it's memory with SystemRecueCD memtest for 24 hours and nothing was wrong. So I'm thinking the CPU and memory are probably okay.
   
  Is there a program to diagnose HW in Linux and find the failed part?
   
  How would I test the HD surface for bad sectors in ubuntu or any other Linux distro? Remember that I don’t want to check the files system, instead I want to check the disk surface, so I’m thinking fsck is not the right tool.
   
  Thanks in advance.
   
  :confused:

---

### Post by jvl on 2006-06-22
The rule of thumb is, when hard disk's electronics can't remap bad sectors anymore and they become visible, the disk should be replaced.

in linux use command "badblocks /dev/hda" 
The command output is the sequence number of bad sector.

then you could view the SMART log from the disk using smartcl from smartmontools (apt-get install smartmontools)

smartctl -H /dev/hda
smartctl --all /dev/hda

you could post the command outputs here for your fellow ubuntuers to see.

Have a nice day.

---

### Post by ssalman on 2006-06-22
Thanks jvl, I will give it a try this weekend and report back my findings.

BTW, is there a CheckIt clone for Linux?

---

### Post by lamego on 2006-06-22
Don't spuch much time trying to look at the problem. If you have bad sectors it is very likely that the damaged area on the disk will increase over the time. Just replace the disk.

---

### Post by ssalman on 2006-06-24
Okay, I downloaded the [INSERT]("http://www.inside-security.de/insert_en.html") CD to run "badblocks /dev/hda" and it  took a little over 4 hours, but the output shown below show that my HD have many bad blocks. My question is: are those blocks marked bad now? is it safe to reformat the HD and install Windows on it? or is this only a diagnosis tool which does not mark the bad sectors?

```

90624
90652
90653
90654
90655
136400
136440
136441
136442
136443
137264
137288
137289
137290
137291
8491264
8491320
8491321
8491322
8491323
10855472
10855520
10855521
10855522
10855523
17781976
17782036
17782037
17782038
17782039
17783112
17783124
17783125
17783126
17783127
20143240
20143260
20143261
20143262
20143263
29926928
29926980
29926981
29926982
29926983
31703928
31703948
31703949
31703950
31703951

```


Next I ran "smartctl -H /dev/hda". and here is the output:

```

smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/]("http://smartmontools.sourceforge.net/")

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE
UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   001   001   112    Old_age
Always   FAILING_NOW 27848

```

so the drive is PASSED?? does that mean it is okay to use it?

next was "smartctl -all /dev/hda"
```

smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/]("http://smartmontools.sourceforge.net/")

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar family
Device Model:     WDC WD400BB-75AUA1
Serial Number:    WD-WMA6R4039805
Firmware Version: 18.20D18
User Capacity:    40,020,664,320 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jun 24 01:07:19 2006 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                       was suspended by an
interrupting command from host.
                                       Auto Offline Data Collection: Enabled.
Self-test execution status:      (  24) The self-test routine was aborted by
                                       the host.
Total time to complete Offline
data collection:                 (2040) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                       Auto Offline data collection
on/off support.
                                       Suspend Offline collection upon new
                                       command.
                                        Offline surface scan supported.
                                       Self-test supported.
                                       No Conveyance Self-test supported.
                                       No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                       power-saving mode.
                                       Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                       No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  32) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE
UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   196   194   051    Pre-fail
Always       -       85
  3 Spin_Up_Time            0x0007   108   102   021    Pre-fail
Always       -       3441
  4 Start_Stop_Count        0x0032   099   099   040    Old_age
Always       -       1689
  5 Reallocated_Sector_Ct   0x0032   001   001   112    Old_age
Always   FAILING_NOW 27848
  7 Seek_Error_Rate         0x000b   200   200   051    Pre-fail
Always       -       0
  9 Power_On_Hours          0x0032   063   063   000    Old_age
Always       -       27684
 10 Spin_Retry_Count        0x0013   100   099   051    Pre-fail
Always       -       1
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail
Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age
Always       -       1626
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age
Always       -       25614
197 Current_Pending_Sector  0x0012   200   170   000    Old_age
Always       -       0
198 Offline_Uncorrectable   0x0012   199   172   000    Old_age
Always       -       12
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age
Always       -       0
200 Multi_Zone_Error_Rate   0x0009   199   198   051    Pre-fail
Offline      -       9

SMART Error Log Version: 1
ATA Error Count: 359 (device log contains only the most recent five errors)
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

Error 359 occurred at disk power-on lifetime: 376 hours (15 days + 16 hours)
  When the command that caused the error occurred, the device was
active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 19 87 c7 e3  Error: UNC at LBA = 0x03c78719 = 63407897

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 08 18 87 c7 e3 00      03:49:03.900  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:59.300  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:54.500  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:49.750  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:44.800  READ SECTOR(S)

Error 358 occurred at disk power-on lifetime: 376 hours (15 days + 16 hours)
  When the command that caused the error occurred, the device was
active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 19 87 c7 e3  Error: UNC at LBA = 0x03c78719 = 63407897

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 08 18 87 c7 e3 00      03:48:59.300  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:54.500  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:49.750  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 d8 20 87 c7 e3 00      03:48:44.800  READ SECTOR(S)

Error 357 occurred at disk power-on lifetime: 376 hours (15 days + 16 hours)
  When the command that caused the error occurred, the device was
active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 19 87 c7 e3  Error: UNC at LBA = 0x03c78719 = 63407897

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 08 18 87 c7 e3 00      03:48:54.500  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:49.750  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 d8 20 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 00 f8 86 c7 e3 00      03:48:39.500  READ SECTOR(S)

Error 356 occurred at disk power-on lifetime: 376 hours (15 days + 16 hours)
  When the command that caused the error occurred, the device was
active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 19 87 c7 e3  Error: UNC at LBA = 0x03c78719 = 63407897

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 08 18 87 c7 e3 00      03:48:49.750  READ SECTOR(S)
  20 00 08 18 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 d8 20 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 00 f8 86 c7 e3 00      03:48:39.500  READ SECTOR(S)
  20 00 08 f0 86 c7 e3 00      03:48:39.500  READ SECTOR(S)

Error 355 occurred at disk power-on lifetime: 376 hours (15 days + 16 hours)
  When the command that caused the error occurred, the device was
active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 19 87 c7 e3  Error: UNC at LBA = 0x03c78719 = 63407897

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 00 08 18 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 d8 20 87 c7 e3 00      03:48:44.800  READ SECTOR(S)
  20 00 00 f8 86 c7 e3 00      03:48:39.500  READ SECTOR(S)
  20 00 08 f0 86 c7 e3 00      03:48:39.500  READ SECTOR(S)
  20 00 50 20 87 c7 e3 00      03:48:39.450  READ SECTOR(S)

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining
LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               80%         0         -

Device does not support Selective Self Tests/Logging

```

what can I make out of all of this?


Thanks for all the help.

---

### Post by jvl on 2006-06-26
badblocks only shows bad sectors, it doesn't mark them as bad. There is a parameter to the mkfs command, so you could feed this list in, so these sectors don't get used. 

If I were you, I'd throw the disk away immediately. 

See the smartlog: UDMA errors, offline errors, non recoverable errors ... it's not worth to risk further data loss ...

---

### Post by ssalman on 2006-06-26
Thanks JVL.

This machine have been replaced with a new one after it have failed so many times, and now I'm considering using it for free public use at a place that I provide technical help with. Basically it will have a winXP, office, and connect to the internet. Data loss is not a big deal, as long as I don't have to support (by reinstall the OS) every few weeks like I used to do. Do you still think I need to replace the HD, or shoulf the mkfs method fix the majority of these issues?

Again thanks for all the help.

---

### Post by jvl on 2006-06-27
More bad blocks would follow.  There have also been UDMA errors, meaning the disk would be terribly slow. I'd replace the disk myself.

---

### Post by ssalman on 2006-06-27
Thank you very much for your help.

---

### Post by jvl on 2006-06-28
You're welcome.

---

