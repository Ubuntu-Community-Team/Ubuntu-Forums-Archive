---
title: "Busybox (inframs) error."
date: 2012-03-17
forum: General Help
---

### Post by F.G. on 2012-03-17
hi everyone,
i recently tried to boot up my computer and got this error. the machine dropped to an 'inframs' console with only a few commands. I understand that this is some kind of thing which exists after grub has loaded, and before moving into the actual OS. i tried running the previous kernels though got the same error. i also tried typing 'exit' in the hope that it would exit the console and boot normally, alas it froze after outputting a few messages. i tried booting in recovery mode and got a verbose output, which looked like something was spinning, and it was having trouble mounting a drive.

my machine dual-boots (or at least used to) windows xp and ubuntu 11.10. it is partitioned into ntfs and ext4 with three linux partitions: swap, /, and /home. when i used a live distro to get stuff off the hard disk the /home partition would not mount and therefore was not readable.

so, does anyone know how i fix this issue?? or failing that, and doing a fresh install, how i might be able to get data off the /home before doing that?

thanks for all and any responses, sorry i don't have more specific error messages, or logging info , though for obvious reasons screenshots/copy and pasting is not possible.

thanks,
F.G.

---

### Post by matt_symes on 2012-03-17
Hi

If you have a separate home partition then you can reinstall Ubuntu into the root partition. That's one of the benefits of a separate home partition. Just remember to format the root partition only and not the home partition. You need to select the advanced option on the partition page on the installer to do this.

As for your Busybox error, can you post a screen shot of what is has on the screen when it fails ? It sounds like it may not be able to find the root partition but this is only a guess without looking.

Kind regards

---

### Post by Cheesehead on 2012-03-17
Dropping to busybox can happen for a number of reasons. It means that the kernel and initrd sucessfully loaded from your /boot...but some problem prevent loading of the main system.

It could be a misconfigured grub, pointing to a root (/) directory that doesn't exist.
It could be a hardware failure, causing the new / to not exist.
It could be a corrupted install, causing /sbin/init to not exist or be unreadable.
It could be a misconfigured install, causing /sbin/init to be in a different location.
It could be a corrupted filesystem, enabling you to run fsck on the unmounted root filesystem.

The purpose of dropping to busybox is to enable you to identify which of these (or something else) is the real problem, and -if possible- repair it. You can also exit busybox (CTRL+D) and try to continue the boot sequence, preferably after such a repair.

---

### Post by raja.genupula on 2012-03-18
@matt_sysmes , lol you remember ? you teach me Busy Box .

well @op please the log for knowing what cause the Error .

---

### Post by F.G. on 2012-03-19
Thanks for your replies, i've not had access to the laptop in question for the last couple of days, so havn't been able o get any more info. i will post it when i have it. my main issue here is that if i do need to do a fresh install (which will probably be what ends up happening)i will probably still not be able to access /home, as i can't seem to access it when running a live distro. regarding the original install, it was a clean 10.04 install which i 'upgraded' to 11.10  about six months ago, any has been working fine up until now, so i think it's unlikely to be a mis-configuration issue / install issue.

thanks again for the responses, i'll post up some log info when i get hold of it (i wonder of not being able to  mount /home would prevent the system from booting up as it has account info in? then again, i also can't boot to the recovery console, which i guess should be logging into root).

---

### Post by F.G. on 2012-04-04
hello everyone, so, i finally got hold of the laptop again (sorry for prematurely starting this thread) and am going to have another go at sorting it out. here are some pics:

the verbose output spinning before dropping to the inframs shell:
[http://img198.imageshack.us/img198/7876/spinningq.jpg]("http://img198.imageshack.us/img198/7876/spinningq.jpg")

the inframs shell, into which i have entered 'exit':
[http://img18.imageshack.us/img18/8927/inframserror.jpg]("http://img18.imageshack.us/img18/8927/inframserror.jpg")

i should also point out that when i tried Ctr-D i got this same error, although missing the first line of output (the one starting with "init: line 331: can't locate /root/dev/console"). also the caps-lock key light seemed to be flashing throughout this.  the machine dual boots with windows, which is still working.

thanks for any suggestions for what i should try, or any insightful reading of these messages. i have the suspicion that it may be the symptom of a corrupt hard disk.

---

### Post by matt_symes on 2012-04-05
Hi

You are getting device ready errors on your hard drive.

You are also having a kernel panic when writing to the drive. The kernel itself is crashing. This is not a good sign.

Before doing anything, i would boot into a liveCD/USB and run a SMART check on the disc itself. This will check the integrity of the hardware itself.

From a terminal in a live CD session

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

Change sda as required for your set up.

After it has finished

```
sudo smartctl -a /dev/sda
```

and post the output back here.

Do that before anything. This may well be hardware. How old is the drive ?

Also can you boot into an older kernel and when did this start happening (recently, after a kernel update) ?

Kind regards

---

### Post by F.G. on 2012-04-05
hi matt,
thanks for your detailed reply, i have followed you're instructions, and here is the output, sorry if it's a bit long (also sorry it took me a while to get back to you, i was at work):
```
 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST9160827AS
Serial Number:    5RF13581
Firmware Version: 3.AAA
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Apr  5 18:28:32 2012 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 116)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:          ( 426) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  64) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   100   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1916
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       141260476
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8160
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       2019
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       1110
190 Airflow_Temperature_Cel 0x0022   055   039   045    Old_age   Always   In_the_past 45 (0 15 61 11)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       383
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       967
193 Load_Cycle_Count        0x0022   070   070   000    Old_age   Always       -       61381
194 Temperature_Celsius     0x001a   045   061   000    Old_age   Always       -       45 (0 11 0 0)
195 Hardware_ECC_Recovered  0x0012   067   055   000    Old_age   Always       -       149952893
197 Current_Pending_Sector  0x0010   100   100   000    Old_age   Offline      -       1
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       1
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       1
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 1
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

Error 1 occurred at disk power-on lifetime: 34 hours (1 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 46 57 73 40  Error: ICRC, ABRT at LBA = 0x00735746 = 7558982

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 27 57 73 40 00      00:38:14.404  READ DMA EXT
  25 00 20 47 57 73 40 00      00:38:14.402  READ DMA EXT
  25 00 20 67 57 73 40 00      00:38:14.401  READ DMA EXT
  25 00 20 87 57 73 40 00      00:38:14.400  READ DMA EXT
  25 00 20 a7 57 73 40 00      00:38:14.399  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%      8158         220106913

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

the hard disk is not that old, it is a hard disk i got in new york about four years ago (and used as a replacement about two years ago, when the original started to fail ). as far as i know i did nothing like an upgrade, or anything that might have made a change before rebooting it, also i can't start it with the previous kernel. 

thanks for any help, or suggestions, although i think this may very well be a hardware issue.

---

### Post by matt_symes on 2012-04-08
Hi

> Self-test execution status:      ( 116)    The previous self-test completed having
                    the read element of the test failed.

It looks like the hard drive has failed.

Kind regards

---

### Post by F.G. on 2012-04-08
thanks matt, i figured that it was probably that, i guess i'm going to format it and reinstall, even though the hard disk is probably finished and it will probably recur. hope you're having fun over the bank holiday weekend.

---

