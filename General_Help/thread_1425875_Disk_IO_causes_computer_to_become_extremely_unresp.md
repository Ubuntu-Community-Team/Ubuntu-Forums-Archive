---
title: "Disk IO causes computer to become extremely unresponsive"
date: 2010-03-09
forum: General Help
---

### Post by yang on 2010-03-09
Whenever I do something like copy a file from one location to another, my Ubuntu 9.10 system becomes extremely unresponsive. The mouse locks up for periods at a time, windows lock up and turn grayscale, etc. I don't seem to have this problem with other systems, Ubuntu or Windows. AFAIK, the system isn't swapping very intensely -- the system activity meter GNOME panel widget doesn't show memory as being maxed out. This is all on a machine with 2G RAM. Any help? Thanks in advance.

---

### Post by doas777 on 2010-03-09
try doing a memtest

---

### Post by yang on 2010-03-09
I just ran memtest, but it didn't report anything was wrong.

---

### Post by doas777 on 2010-03-09
> **yang said:**
> I just ran memtest, but it didn't report anything was wrong.

ok, then it is likely a deadlock issue. if the mouse locks, usually that means that it's stuck down to the kernel. 
try opening a terminal and running 'iotop' (you may need to install it first), but monitor what procs are doing the disk IO when it slows/locks.  

have you manually done an fschk on the disk? how about a SMART readout?

---

### Post by yang on 2010-03-09
I had already used iotop -- the process is just whatever's using the disk. E.g., if I'm copying a file, then it's cp. If I'm installing Windows in virtualbox, then it's virtualbox. Etc.

I did an fsck the last time I rebooted, which was a few days ago. In any case this problem has persisted for as long as I can remember (>1 year).

Not sure what to look for in the SMART readout....

---

### Post by ibuclaw on 2010-03-09
> **yang said:**
> I had already used iotop -- the process is just whatever's using the disk. E.g., if I'm copying a file, then it's cp. If I'm installing Windows in virtualbox, then it's virtualbox. Etc.

I did an fsck the last time I rebooted, which was a few days ago. In any case this problem has persisted for as long as I can remember (>1 year).

Not sure what to look for in the SMART readout....

How much RAM / Swap do you have?

You could try changing scheduler for your system, as quite a few people have had success in that.

```
echo "deadline" | sudo tee /sys/block/sda/queue/scheduler
```

Valid options are:
[LIST]
[*]noop
[*]anticipatory
[*]deadline
[*]cfq
[/LIST]
The default in Ubuntu (and most other distributions) is cfq.

To make this permanent, you would put:
```
elevator=deadline
```
Inside your grub default option config (with grub2, this is in /etc/default/grub). Then run 'update-grub'

Regards
Iain

---

### Post by doas777 on 2010-03-10
SMART is a interface for monitoring the vital statistics about the health of a hard disk. in windows I use Speedfan to read smart info off my drives, but in ubuntu I use SmartMonTools [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by denver on 2010-03-10
The linux kernel allocaes the same I/O priority to all operations, regardless of importance. Usualy when you copy a large file you dont really want to stand arround looking at the progress bar, so you really don't care all that much it it finishes in 10 seconds or 5 minutes.

The problem is that the kernel does not make this distinction. You can however tell it in which class it should be placed. Use:

```
ionice -c3 <COMMAND>
```

or

```
ionice -c3 -p<PID>
```


to start a command, or to place an existing one in the "idle" class. There are 4 classes you can specify using ionice:

0 - no class
1 - real time
2 - best effort
3 - idle

I use the "idle" class, as i only want a greedy I/O operation to use the disk whenever i don't need it. This way i can still use my PC while creating a VirtualBox virtual Disk :) (what a tongue twister).

Best of luck!

EDIT: if you start a terminal with the ionice command, all other applications started in that terminal will inherit the class you specified:

```
ionice -c3 /bin/bash
```

All other processes started in that terminal will use the idle class.

---

### Post by yang on 2010-03-21
doas777: I used smartmontools, and it says everything's fine:

```

$ sudo smartctl --all /dev/sda2
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar T7K500
Device Model:     Hitachi HDT725025VLA380
Serial Number:    VFG111R5EXB4JF
Firmware Version: V5DOA73A
User Capacity:    250,000,000,000 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Sun Mar 21 15:09:07 2010 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (4949) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  83) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   161   161   050    Old_age   Offline      -       196
  3 Spin_Up_Time            0x0007   135   135   024    Pre-fail  Always       -       329 (Average 224)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       45
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   134   134   020    Old_age   Offline      -       32
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       21144
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       45
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       94
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       94
194 Temperature_Celsius     0x0002   153   153   000    Old_age   Always       -       39 (Lifetime Min/Max 20/44)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         1         -
# 2  Short captive       Completed without error       00%         1         -

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

$ sudo smartctl --test=long /dev/sda2
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 83 minutes for test to complete.
Test will complete after Sun Mar 21 16:34:43 2010

Use smartctl -X to abort test.

$ sudo smartctl --attributes --log=selftest /dev/sda2
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   161   161   050    Old_age   Offline      -       196
  3 Spin_Up_Time            0x0007   135   135   024    Pre-fail  Always       -       329 (Average 224)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       45
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   134   134   020    Old_age   Offline      -       32
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       21145
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       45
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       94
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       94
194 Temperature_Celsius     0x0002   139   139   000    Old_age   Always       -       43 (Lifetime Min/Max 20/44)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         1         -
# 2  Short captive       Completed without error       00%         1         -

```

---

### Post by yang on 2010-03-21
ibuclaw: I have 2G RAM and 1G swap. It seems wrong that I'd need to switch away from the default scheduler; I'd ideally like to get to the bottom of the current situation.

```

$ free
             total       used       free     shared    buffers     cached
Mem:       2055724    1607476     448248          0      34468     422060
-/+ buffers/cache:    1150948     904776
Swap:       979924     376824     603100

$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123       30394   243159840   83  Linux

$ vmstat 1
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0 376824 448488  34408 422024    0    1    10    22    6   23  4  1 95  1
 0  0 376824 448480  34408 422048    0    0     0     0  676 1203  2  0 98  0
 0  0 376824 448480  34408 422048    0    0     0     0  627 1109  2  0 98  0
 0  0 376824 448480  34408 422048    0    0     0     0  657 1162  1  0 99  0
 0  0 376824 448480  34408 422048    0    0     0     0  625 1121  2  0 98  0
 0  0 376824 448480  34408 422048    0    0     0     0  654 1187  2  0 98  0
 0  0 376824 448480  34408 422048    0    0     0     0  602 1099  1  0 99  0
 0  0 376824 448480  34408 422048    0    0     0     0  644 1169  3  0 96  0

```

---

### Post by yang on 2010-03-21
denver: I know about ionice, but even running "ionice -c 3 cp ..." still results in the same slow-downs....

---

### Post by krusbjorn on 2010-06-04
Any luck yet?

I have the same problem with my new Western Digital Caviar 1TB. The system is unaffeced when my other hard drive (an old Maxtor) is working, but as soon as there is activity on the WD, everything becomes very unresponsive. This of course also slows down the overall performance, since starting programs etc also is slowed down by this.

I was hoping the update to 10.04 would solve this, but the problem persists.

---

### Post by ibuclaw on 2010-06-04
> **krusbjorn said:**
> Any luck yet?

I have the same problem with my new Western Digital Caviar 1TB. The system is unaffeced when my other hard drive (an old Maxtor) is working, but as soon as there is activity on the WD, everything becomes very unresponsive. This of course also slows down the overall performance, since starting programs etc also is slowed down by this.

I was hoping the update to 10.04 would solve this, but the problem persists.

Have you tried any of the suggestions in thread? Changing the scheduler of the block device?

---

### Post by krusbjorn on 2010-06-04
Yes, I tried it. Didn't work I'm afraid. I also ran SMART-tests on the HD, with no errors reported.

Found this though, seems to be it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

---

### Post by ibuclaw on 2010-06-04
> **krusbjorn said:**
> Yes, I tried it. Didn't work I'm afraid. I also ran SMART-tests on the HD, with no errors reported.

Found this though, seems to be it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

Is the 1TB disk sda or sdb? (you'll have to exchange the 'sda' bit in:
```
echo "deadline" | sudo tee /sys/block/sda/queue/scheduler
```
With the device that is causing issues.

Also, what filesystem are you using? Does it span across the whole disk?

---

### Post by krusbjorn on 2010-06-04
> **ibuclaw said:**
> Is the 1TB disk sda or sdb? (you'll have to exchange the 'sda' bit in:
```
echo "deadline" | sudo tee /sys/block/sda/queue/scheduler
```
With the device that is causing issues.

Also, what filesystem are you using? Does it span across the whole disk?

Thank you Ibuclaw for your reply :). Yes, it is sda.

Here is the partition table:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        2067     1951867    5  Extended
/dev/sda3            2068       14225    97659135    7  HPFS/NTFS
/dev/sda4           14226      121601   862497720   83  Linux
/dev/sda5            1825        2067     1951866   82  Linux swap / Solaris
```

Sda1 is mounted at / and contains the operating system. Sda2 is an extended partition containing sda5 (swap). Sda3 is my WindowsXP installation and Sda4 is mounted at /home.

---

### Post by ibuclaw on 2010-06-04
> **krusbjorn said:**
> Thank you Ibuclaw for your reply :). Yes, it is sda.

Here is the partition table:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        2067     1951867    5  Extended
/dev/sda3            2068       14225    97659135    7  HPFS/NTFS
/dev/sda4           14226      121601   862497720   83  Linux
/dev/sda5            1825        2067     1951866   82  Linux swap / Solaris
```

Sda1 is mounted at / and contains the operating system. Sda2 is an extended partition containing sda5 (swap). Sda3 is my WindowsXP installation and Sda4 is mounted at /home.

Ext3 or Ext4 ?

---

### Post by krusbjorn on 2010-06-04
> **ibuclaw said:**
> Ext3 or Ext4 ?

Sda1 is ext3 and sda4 is ext4. Earlier both were ext4 but when I did a fresh 10.04 install hoping to resolve the problem I tried ext3 for the system partition. Performance is still the same though.

---

### Post by ibuclaw on 2010-06-04
> **krusbjorn said:**
> Sda1 is ext3 and sda4 is ext4. Earlier both were ext4 but when I did a fresh 10.04 install hoping to resolve the problem I tried ext3 for the system partition. Performance is still the same though.

You *could* try: [http://sdennie.ubuntuforums.org/showthread.php?t=839998](http://sdennie.ubuntuforums.org/showthread.php?t=839998)

Seeing if delaying write allocation helps.

---

### Post by RainmanATX on 2010-09-10
Howdy all!  I have been running Ubuntu 8.04LTS since about late 2008.  I got iotop working, just google iotop_0.2-2_all.deb for 8.04, and has gave me some info as to where my thrashing issues are coming from.  I have been having a general thrashing problem since about mid-2009, but since my Ubuntu sys is used as a general desktop, I just step away for a few min and it sorts itself out.  Haha, my days of internet usage at 2400 baud taught me that trick!  Ok, enough with the backstory.  Iotop is showing a command, with my userid and not root, "--channel=6319.0xAXXXXXX.XXXXXXXXX", the A represents a letter, usually the first several in the alphabet, those used in hex I guess, the X's represent numbers.  I have tried using google, which does not search for symbols, grrr, to no avail.  Any ideas?

P.S. - I'm rather new to forums, apologies for any edicate issues.  ):P )

***Update***  
Was using Chrome about an hour ago, decided to check out some extensions.  Installed this one; [https://chrome.google.com/extensions/detail/bfbmjmiodbnnpllbbbfblcplfjjepjdn](https://chrome.google.com/extensions/detail/bfbmjmiodbnnpllbbbfblcplfjjepjdn)

HDD went into a thrashing fit!  Not until I pulled up the chrome task manager and showed that it was simply building in resource usage.  Uninstalled it, thrashing fit ended, but the number is 18322 now instead of 6319.  Tried to find a size setting on how much HDD space chrome can use for its cache, could not find it.  Well, will avoid that extension for now, problem still occurring, just thought I'd share, might give someone a brain-fart.  :-D

---

### Post by ibuclaw on 2010-09-10
By the power of greyskull, thread closed.

---

