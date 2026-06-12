---
title: "Hard drive issue at boot"
date: 2010-09-06
forum: General Help
---

### Post by Aflo on 2010-09-06
Hello !

I run Ubuntu 10.04 (upgrade from 9.04 and 9.10) on a Dell Inspiron 1525 laptop.
 A few weeks ago, I started to have issues when booting: the computer remains stuck for a long time on the screen showing "Boot from (hd0,4) ext3...". Sometimes it does boot in the end, while sometimes it just shows a black screen with a single flashing white underscore... Sometimes, my computer seems to boot normally.

I have looked in dmesg. Here is an extract of the parts which (I think) show the errors:
```
[   93.070464] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   93.070468] ata1.00: irq_stat 0x40000008
[   93.070473] ata1.00: failed command: READ FPDMA QUEUED
[   93.070481] ata1.00: cmd 60/00:00:41:02:59/01:00:16:00:00/40 tag 0 ncq 131072 in
[   93.070483]          res 41/40:00:8c:02:59/00:00:16:00:00/40 Emask 0x409 (media error) <F>
[   93.070488] ata1.00: status: { DRDY ERR }
[   93.070491] ata1.00: error: { UNC }
[   93.075186] ata1.00: configured for UDMA/133
[   93.075206] sd 0:0:0:0: [sda] Unhandled sense code
[   93.075210] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   93.075222] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   93.075226] Descriptor sense data with sense descriptors (in hex):
[   93.075228]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   93.075236]         16 59 02 8c 
[   93.075240] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   93.075244] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 16 59 02 41 00 01 00 00
[   93.075253] end_request: I/O error, dev sda, sector 374932108
[   93.075256] Buffer I/O error on device sda5, logical block 33030524
[   93.075259] Buffer I/O error on device sda5, logical block 33030525
[   93.075261] Buffer I/O error on device sda5, logical block 33030526
[   93.075263] Buffer I/O error on device sda5, logical block 33030527
[   93.075266] Buffer I/O error on device sda5, logical block 33030528
[   93.075268] Buffer I/O error on device sda5, logical block 33030529
[   93.075270] Buffer I/O error on device sda5, logical block 33030530
[   93.075273] Buffer I/O error on device sda5, logical block 33030531
[   93.075275] Buffer I/O error on device sda5, logical block 33030532
[   93.075277] Buffer I/O error on device sda5, logical block 33030533
[   93.075289] ata1: EH complete
```Lines like
```
[   93.070464] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   93.070468] ata1.00: irq_stat 0x40000008
[   93.070473] ata1.00: failed command: READ FPDMA QUEUED
[   93.070481] ata1.00: cmd 60/00:00:41:02:59/01:00:16:00:00/40 tag 0 ncq 131072 in
[   93.070483]          res 41/40:00:8c:02:59/00:00:16:00:00/40 Emask 0x409 (media error) <F>
[   93.070488] ata1.00: status: { DRDY ERR }
[   93.070491] ata1.00: error: { UNC }
[   93.075186] ata1.00: configured for UDMA/133

```are repeated several times, and the number of times they are repeated seems to vary each time I boot. :confused:
Besides, such problems occured with different kernels in Ubuntu 9.10 and 10.04.

I have also tried booting Windows, it seems to work, but I never use it...

Thinking that it may be a hard drive or filesystem issue, I ran fsck from a live CD. It did not detect any problem.
Maybe my hard drive is dying ? :cry: However, this computer is only one year and a few months old...

I would appreciate any help or idea regarding the nature of my problem.
Thank you very much in advance !!

---

### Post by bsmith1051 on 2010-09-17
I'm having the same issue.  I'd previously read it might be a problem with kernel 2.6.32-x (like in Lucid, which I'm running) and would be fixed in 2.6.34.x (i.e, Maverick).  I haven't had a chance to upgrade yet, though.

---

### Post by Aflo on 2010-09-19
Thank you for your reply. I am indeed running a 2-6-32-x kernel too. However, my problems appeared after one of the last Karmic upgrades. Wasn't it still a 2-6-31-x kernel then ? Unfortunately I don't remember. 

My problems are still the same, however, now, fsck has detected errors (I had to use the rescue superblock, and then I got incorrect block counts). I told it to correct the mistakes, but nothing really changed after that.

Maybe I should try to upgrade to Maverick if this issue is linked to the kernel version...
I am really no Linux expert, and I thought that it might be a problem with my hard drive, so this is giving me some hope.

---

### Post by dlm8751 on 2010-10-06
Same issue after taking updates going from 2.6.32-25 from 2.6.32-21(64 bit). System is unusable. Hard drive light is on hard.

Oct  6 18:12:04 new-tera kernel: [  402.540811] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
Oct  6 18:12:04 new-tera kernel: [  402.545744] ata1.00: irq_stat 0x40000008
Oct  6 18:12:04 new-tera kernel: [  402.545750] ata1.00: failed command: READ FPDMA QUEUED
Oct  6 18:12:04 new-tera kernel: [  402.545762] ata1.00: cmd 60/08:00:68:40:46/00:00:00:00:00/40 tag 0 ncq 4096 in
Oct  6 18:12:04 new-tera kernel: [  402.545768]          res 41/40:00:6d:40:46/00:00:00:00:00/40 Emask 0x409 (media error) <F>
Oct  6 18:12:04 new-tera kernel: [  402.545776] ata1.00: status: { DRDY ERR }

---

### Post by bsmith1051 on 2010-10-08
I upgraded my laptop to Maverick and I think it fixed the issue; totally different kernel rev?  Also, I'm not on 64-bit, sorry, didn't notice that part of your earlier post.

---

### Post by bsmith1051 on 2010-10-08
> **dlm8751 said:**
> Same issue after taking updates going from 2.6.32-25 from 2.6.32-21(64 bit).
Huh? from 32-25 **to** 32-21?  isn't that a downgrade?  or, did you just reverse them?  It would be useful to know what previous kernel rev did not have the issue.

---

### Post by psusi on 2010-10-08
Your disk has bad sectors.  You should run the SMART tests in the disk utility on it.

---

### Post by Aflo on 2010-10-09
Hello !
Thank you for your replies. I did a fresh install of Maverick Beta about two weeks ago. My system had got stuck in a routine fsck, and I was beginning to get tired of it...
At first, it worked perfectly, and I thought the problem was solved. However, after a few reboots, it got slower, and I started getting the same error messages again !
I ran the SMART tests as suggested by psusi (both short version and long version): both results seemed OK. However, the errors are mentioned in the file "Smartctl output":
```

smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA family
Device Model:     WDC WD2500BEVT-75ZCT2
Serial Number:    WD-WXA0A69H0553
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Oct  9 14:43:40 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (7500) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  90) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   187   186   051    Pre-fail  Always       -       13337
  3 Spin_Up_Time            0x0027   186   185   021    Pre-fail  Always       -       1675
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       908
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1385
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       903
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       4574
194 Temperature_Celsius     0x0022   096   089   000    Old_age   Always       -       51
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       65
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   099   099   000    Old_age   Always       -       1365
241 Total_LBAs_Written      0x0032   127   127   000    Old_age   Always       -       73740091287556
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       1767078732

SMART Error Log Version: 1
ATA Error Count: 1088 (device log contains only the most recent five errors)
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

Error 1088 occurred at disk power-on lifetime: 1382 hours (57 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 71 be 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 38 71 be 19 08      00:02:42.852  READ FPDMA QUEUED
  ef 10 02 00 00 00 00 08      00:02:42.852  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      00:02:42.852  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:02:42.850  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:02:42.849  SET FEATURES [Set transfer mode]

Error 1087 occurred at disk power-on lifetime: 1382 hours (57 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 71 be 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 38 71 be 19 08      00:02:38.817  READ FPDMA QUEUED
  60 98 00 28 7e 57 07 08      00:02:38.815  READ FPDMA QUEUED
  60 20 00 28 85 e9 06 08      00:02:38.805  READ FPDMA QUEUED
  60 68 00 48 86 e9 06 08      00:02:38.791  READ FPDMA QUEUED
  60 10 00 e0 9f 22 07 08      00:02:38.790  READ FPDMA QUEUED

Error 1086 occurred at disk power-on lifetime: 1382 hours (57 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 71 be 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 38 71 be 19 08      00:02:31.809  READ FPDMA QUEUED
  ef 10 02 00 00 00 00 08      00:02:31.809  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      00:02:31.809  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:02:31.806  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:02:31.806  SET FEATURES [Set transfer mode]

Error 1085 occurred at disk power-on lifetime: 1382 hours (57 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 71 be 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 38 71 be 19 08      00:02:27.363  READ FPDMA QUEUED
  ef 10 02 00 00 00 00 08      00:02:27.363  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      00:02:27.363  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:02:27.360  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:02:27.360  SET FEATURES [Set transfer mode]

Error 1084 occurred at disk power-on lifetime: 1382 hours (57 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 39 71 be 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 38 71 be 19 08      00:02:24.003  READ FPDMA QUEUED
  ef 10 02 00 00 00 00 08      00:02:24.003  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 00 08      00:02:24.003  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:02:24.001  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:02:24.001  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1384         -
# 2  Short offline       Completed without error       00%      1382         -
# 3  Short offline       Completed without error       00%         0         -
# 4  Short offline       Completed without error       00%         0         -
# 5  Short offline       Completed without error       00%         0         -
# 6  Short offline       Completed without error       00%         0         -
# 7  Short offline       Completed without error       00%         0         -
# 8  Short offline       Completed without error       00%         0         -
# 9  Short offline       Completed without error       00%         0         -

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

```I still do not know what to do...

---

### Post by psusi on 2010-10-09
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       65

You have 65 bad sectors.  For some reason your drive does not stop and report the location of the first one when doing the long self test.  It seems to skip over the bad sectors it already knows about during the self test.  The first thing you should do is backup any important data you can still get off the drive.  Then you need to locate the bad sectors and attempt to write to them.  This will either work if nothing is physically wrong with the medium, or will force the sector to be reallocated from the spare pool.

Run sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct

---

### Post by MisterGaribaldi on 2010-10-09
Well, from the output of smart, I'd say you're looking at a hard drive failure *in progress* and that it's continuing to get worse.

Therefore, I believe it's "back up your data and get a new hard drive" time.

---

### Post by psusi on 2010-10-09
Sometimes you can get a group of bad sectors if they were in the middle of being written to when you lost power.  In that case, the medium is fine, it's just the data got corrupted.  If that is the case, overwriting them will fix the problem and there's nothing wrong with the drive.

---

### Post by Aflo on 2010-10-16
Hello !
Sorry for replying late, I was travelling last week. I have tried sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct, but it was taking so long that I stopped it and ran sudo dd if=/dev/sda5 of=/dev/null bs=512 iflag=direct and sudo dd if=/dev/sda6 of=/dev/null bs=512 iflag=direct (sda5 is my "/" partition, and sda6 is my swap). It seems that these two partitions were integrally copied without problems.
Running this command on my "/home" partition or on the whole disk is going to be much longer.
Besides, the fact that I reinstalled everything recently and started having the same problems again seems to hint at a hardware problem, doesn't it ?
Thank you for your help !

---

### Post by Aflo on 2010-10-17
Here are some new errors mentioned in the file "Smartctl output":
```
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA family
Device Model:     WDC WD2500BEVT-75ZCT2
Serial Number:    WD-WXA0A69H0553
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Oct 17 19:18:00 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (7500) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  90) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   188   186   051    Pre-fail  Always       -       13802
  3 Spin_Up_Time            0x0027   186   185   021    Pre-fail  Always       -       1666
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       916
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1409
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       911
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       4584
194 Temperature_Celsius     0x0022   122   089   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       67
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   099   099   000    Old_age   Always       -       1389
241 Total_LBAs_Written      0x0032   126   126   000    Old_age   Always       -       74307027589200
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       2266817502

SMART Error Log Version: 1
ATA Error Count: 1202 (device log contains only the most recent five errors)
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

Error 1202 occurred at disk power-on lifetime: 1409 hours (58 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:10.863  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:10.863  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:10.862  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:10.862  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:10.861  READ NATIVE MAX ADDRESS EXT

Error 1201 occurred at disk power-on lifetime: 1409 hours (58 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:06.258  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:06.258  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:06.257  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:06.257  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:06.256  READ NATIVE MAX ADDRESS EXT

Error 1200 occurred at disk power-on lifetime: 1409 hours (58 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:02.497  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:02.497  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:02.496  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:02.496  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:02.495  READ NATIVE MAX ADDRESS EXT

Error 1199 occurred at disk power-on lifetime: 1409 hours (58 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:01:59.029  READ DMA EXT
  27 00 00 00 00 00 00 00      00:01:59.029  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:01:59.028  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:01:59.028  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:01:59.027  READ NATIVE MAX ADDRESS EXT

Error 1198 occurred at disk power-on lifetime: 1409 hours (58 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:01:55.593  READ DMA EXT
  27 00 00 00 00 00 00 00      00:01:55.593  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:01:55.591  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:01:55.591  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:01:55.591  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%      1408         -
# 2  Short offline       Completed without error       00%      1408         -
# 3  Extended offline    Completed without error       00%      1384         -
# 4  Short offline       Completed without error       00%      1382         -
# 5  Short offline       Completed without error       00%         0         -
# 6  Short offline       Completed without error       00%         0         -
# 7  Short offline       Completed without error       00%         0         -
# 8  Short offline       Completed without error       00%         0         -
# 9  Short offline       Completed without error       00%         0         -
#10  Short offline       Completed without error       00%         0         -
#11  Short offline       Completed without error       00%         0         -

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

```The number of errors counted in the "error log" increases, and the number of "current pending sectors" has increased from 65 to 67...
And lines like "Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824" look bad, don't they ?

---

### Post by psusi on 2010-10-17
Run sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct skip=12480824 count=1

If you get an I/O error, then run sudo dd if=/dev/zero of=/dev/sda bs=512 oflag=direct count=1 seek=12480824

That will attempt to write zeros to the bad sector.  If you then run the first command again, it should work.  If you then check the smart numbers, you should see one less pending count and may or may not see one more in the reallocated count.  If the reallocated goes up, then the media is physically damaged, if not, then it was just a transient error.

You can repeat this process for all of the bad sectors and if the reallocated count does not go up, then you have repaired the problem and can carry on.  If reallocated goes up, then you have physical damage and need to RMA the drive if it is still under warranty.

---

### Post by efflandt on 2010-10-17
Go to [http://www.wdc.com/](http://www.wdc.com/) and download their DataLifeguard software to test your drive.  Although, if it is out of warranty all the extended test may do is confirm that you have bad sectors.

Normally a hard drive internally reserves space to transparently remap bad sectors to good sectors.  So if you start seeing bad sectors, that is a bad sign that all error sites are used up and it can only get worse.

I had to get a warranty replacement for a 160 GB Scorpio Blue that I had put in an old laptop.  But my boss' grandsons may have been rough with it.  The original drive became trashed, later WinXP refused to boot when this drive started having bad sectors, later WinXP refused to boot again (just a virus that time), then the screen got broken.  Lucid still boots from the warranty replacement once I figured out how to switch nvidia 96 driver to external VGA while only able to view part of laptop display.

---

### Post by Aflo on 2010-10-17
Well, I tried sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct skip=12480824 count=1, and it seems to work (no I/O error)...
Strange, isn't it ? :confused:

Besides, my computer is out of warranty.

---

### Post by Dans564 on 2010-10-17
I would have to agree with mister. That doesn't look very good

---

### Post by psusi on 2010-10-17
> **Aflo said:**
> Well, I tried sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct skip=12480824 count=1, and it seems to work (no I/O error)...
Strange, isn't it ? :confused:

Besides, my computer is out of warranty.

Hrm... well, they have to be there somewhere... drop the skip and count arguments and let it read the entire disk and see where it runs into the bad sector.

---

### Post by Aflo on 2010-10-20
Well, apparently dd can copy all the disk without any error !
```

sudo dd if=/dev/sda of=/dev/null bs=512 iflag=direct
 488397168+0 enregistrements lus
488397168+0 enregistrements écrits
250059350016 octets (250 GB) copiés, 132113 s, 1,9 MB/s

```
Sorry, it's in French !

It's getting stranger and stranger, isn't it ?

---

### Post by psusi on 2010-10-20
Weird.  Check the SMART numbers again?

---

### Post by Aflo on 2010-10-22
Well, I think they have not changed much:
```
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA family
Device Model:     WDC WD2500BEVT-75ZCT2
Serial Number:    WD-WXA0A69H0553
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Oct 22 20:48:09 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (7500) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  90) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   190   186   051    Pre-fail  Always       -       13891
  3 Spin_Up_Time            0x0027   186   185   021    Pre-fail  Always       -       1683
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       921
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1464
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       916
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       4669
194 Temperature_Celsius     0x0022   113   089   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       67
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   099   099   000    Old_age   Always       -       1435
241 Total_LBAs_Written      0x0032   126   126   000    Old_age   Always       -       74307031457644
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       3247543443

SMART Error Log Version: 1
ATA Error Count: 1222 (device log contains only the most recent five errors)
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

Error 1222 occurred at disk power-on lifetime: 1463 hours (60 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:35.259  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:35.259  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:35.258  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:35.258  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:35.257  READ NATIVE MAX ADDRESS EXT

Error 1221 occurred at disk power-on lifetime: 1463 hours (60 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:31.214  READ DMA EXT
  25 00 08 10 30 7a 1c 00      00:02:31.187  READ DMA EXT
  c8 00 18 60 2a 44 08 00      00:02:31.177  READ DMA
  c8 00 08 10 2c 44 08 00      00:02:31.173  READ DMA
  c8 00 08 30 2b 44 08 00      00:02:31.173  READ DMA

Error 1220 occurred at disk power-on lifetime: 1463 hours (60 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:25.158  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:25.158  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:25.157  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:25.157  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:25.156  READ NATIVE MAX ADDRESS EXT

Error 1219 occurred at disk power-on lifetime: 1463 hours (60 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:21.754  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:21.754  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:21.753  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:21.753  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:21.752  READ NATIVE MAX ADDRESS EXT

Error 1218 occurred at disk power-on lifetime: 1463 hours (60 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 38 71 be e0  Error: UNC 8 sectors at LBA = 0x00be7138 = 12480824

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 38 71 be 19 00      00:02:17.552  READ DMA EXT
  27 00 00 00 00 00 00 00      00:02:17.552  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:02:17.551  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      00:02:17.551  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:02:17.550  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%      1408         -
# 2  Short offline       Completed without error       00%      1408         -
# 3  Extended offline    Completed without error       00%      1384         -
# 4  Short offline       Completed without error       00%      1382         -
# 5  Short offline       Completed without error       00%         0         -
# 6  Short offline       Completed without error       00%         0         -
# 7  Short offline       Completed without error       00%         0         -
# 8  Short offline       Completed without error       00%         0         -
# 9  Short offline       Completed without error       00%         0         -
#10  Short offline       Completed without error       00%         0         -
#11  Short offline       Completed without error       00%         0         -

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
I'm beginning to think of reinstalling 9.04 just to see if this is version-related... :confused:

---

