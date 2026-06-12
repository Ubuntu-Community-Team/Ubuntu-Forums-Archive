---
title: "Strange Issue - Hard Drive Unmounts itself"
date: 2006-03-01
forum: General Help
---

### Post by zgerrz on 2006-03-01
While I was working in Ubuntu, for no apparent reason my hdb drive unmounts itself and all its partitions (all ext3 partitions). I'm initally aware of a problem when I see that I get an I/O error from my torrents in Azureus, which usually means insufficient disk space. I check my downloads partition, and it is blank, as well as my music partition. I unmount the partitions (both on /dev/hdb), and can't remount them (filesystem error), even though they have worked for a long time without problems.

I thought the hard drive spontaneously died, so I tried rebooting to see if I could get a better handle on the problem. My computer took longer than usual to get past the BIOS, and GRUB failed to load, throwing an Error 21 code. I reboot again, and my computer freezes during BIOS loading. THIS part has happened before, where my computer sometimes freezes during BIOS booting (happens more often in cold temperature for some odd reason). Now though, the temperature was pretty warm. To get past this, I usually have to press DEL key to get to BIOS setup and then check the settings and save them (even though I don't actually alter any settings). Then usually everything is fine, and it was again in this case. My drives were all OK again. The whole unmounting issue never happened to me before, but the BIOS part has happened before.

So basically, can anyone tell me any theories on why my BIOS acts strangely sometimes? Also, if there is any connection between that and the hdb drive unmounting itself.

On a side question, what kind of protections does Linux or Ubuntu have with regard to drive failure and data recovery? How hard is it to recover data, and can a drive fail out of the blue without any warning signs?

Thanks for reading, and I hope I can get some answers to all of my questions even though I asked so many.

---

### Post by Jason_25 on 2006-03-01
Check for bios updates.  Also run a few passes of memtest 86.

If you can get back to linux, install smartmontools from apt-get and run 
```

sudo smartctl --all /dev/hda

```
To check the drive for problems.

---

### Post by RAOF on 2006-03-01
I haven't had a drive "fail out of the blue".  Mine always start doing a sort of clicking dance "whirrr..... CLICK!  whirrr....  CLICK!" first :)

That said, I wouldn't say that if one of your harddrives died that it was out of the blue!  Also, it could be that your IDE controller is dying in some way.

---

### Post by zgerrz on 2006-03-01
I ran memtest 86 a few weeks ago when I used to run Fedora Core 4. I was advised to do this because I was experiencing random crashes in FC4 using different kernels. Memtest gave me quite a few errors, and people at the FC4 forums told me that most likely my hardware was bad. I wasn't about to go out and buy all new hardware, so I tried Ubuntu and have no real problems up until this issue.

Here are the results from smartmontools
```

zgerrz@ubuntu:~$ sudo smartctl --all /dev/hdb
Password:
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3160023A
Serial Number:    3LJ076KF
Firmware Version: 3.06
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Mar  1 00:11:11 2006 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 ( 430) seconds.
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
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   064   060   006    Pre-fail  Always       -       186194653
  3 Spin_Up_Time            0x0003   097   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       12
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       13349111921
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6898
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       845
194 Temperature_Celsius     0x0022   032   055   000    Old_age   Always       -       32
195 Hardware_ECC_Recovered  0x001a   064   060   000    Old_age   Always       -       186194653
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

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

zgerrz@ubuntu:~$

```

I will look for bios updates now. Just needed to post what info I have at the moment.

---

### Post by RAOF on 2006-03-01
[QUOTE=zgerrz]I ran memtest 86 a few weeks ago when I used to run Fedora Core 4. I was advised to do this because I was experiencing random crashes in FC4 using different kernels. Memtest gave me quite a few errors, and people at the FC4 forums told me that most likely my hardware was bad. I wasn't about to go out and buy all new hardware, so I tried Ubuntu and have no real problems up until this issue.[/QUOTE]
If memtest has failed, then your hardware (probably your RAM) **is** bad! :cry: 

If your RAM is bad, you are guaranteed to have problems.  Nice, difficult to locate random problems.  Sometimes the kernel will crash, sometimes your harddrives will randomly unmount ;).  It is somewhat unlikely, but this could be as bad as actually destroying the data on your harddrive, or overwriting your partition table.  If data in RAM is getting corrupted, practically anything could happen.  I suppose that if you were **extremely** unlucky, the kernel could accidentally flash your BIOS with random data.  Beware!

---

### Post by Jason_25 on 2006-03-01
Good call on the bios.  No flashing with unstable memory.  Don't even bother using the pc until this is worked out.  What are your hardware specs?  You may simply need to adjust the memory settings in your bios.

Since you haven't mentioned it, it sounds like you have some value/generic memory.  This memory is sometimes completely incompatible with certain motherboards and cpus, further complicating the problem.

---

### Post by zgerrz on 2006-03-01
You would think that I have some crap generic memory, but in fact I'm using two 512 MB sticks of Corsair XMS brand memory (PC 3200 SDRAM DDR). It's not cheap memory and it isn't some generic garbage as far as I have seen.

The rest of my relevant specs:

Intel P4 2.8 GHz with HT
Asus P4C800 mobo

---

