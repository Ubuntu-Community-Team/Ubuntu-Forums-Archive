---
title: "HELP me before I have to reboot a frozen PC"
date: 2010-10-19
forum: General Help
---

### Post by Handssolow on 2010-10-19
I want to find if I can recover any useful information to explain the cause of random freezes on one of our PC running 10.10. The PC froze earlier today but I haven't rebooted. I lost Firefox and the toolbars but by chance the terminal was already open and I can input commands.

I'm unable to use gedit nano cat less, to view the log files. I'm not able to use, ubuntu-bug -p linux. Most if not all commands end like this
bash: /usr/bin/less: Input/output error

Very few that I know of give some information, most point to an I/O fault. Previous testing of hard drive for over 2 hours yielded no errors, similarly nothing in Smart. 

Output of dmesg
5932.861974 sd 0:0:0:0: [sda] Result hostbyte=DID_BAD_TARGET driverbyte=Driver_OK
5932.861983 sd 0:0:0:0: [sda] CDB Read(10)28 00 06 86 bc 00 00 08 00
5932.862013 end_request: I/O error,dev sda sector 109493432
5932.862064 sd 0:0:0:0: [sda] unhandled error code
 there are about 3 repeats of this, then another 4 with a different sector number. Repeating dmesg gives other sector numbers. Final line of dmesg is
[6066.692835] end_request: I/O error, dev sda sector 14706739

Output of mount
/dev/sda1 on /type ext4 (rw,errors=remount-ro,commit=0
next are several lines which I think are normal but the final lines are-
mount:warning /etc/mstab is not writeable (read only file system). Its possible that information reported by mount (8) is not up to date. For actual information about the system mount points check /proc/mounts file

Whilst it would be easy to suspect the hard drive all the tests I've done have been negative.

The frozen PC is upstairs with an open terminal. Can any useful information be acquired as to the cause of this problem? I know little about using bash.

---

### Post by edward1978 on 2010-10-19
> **Handssolow said:**
> I want to find if I can recover any useful information to explain the cause of random freezes on one of our PC running 10.10. The PC froze earlier today but I haven't rebooted. I lost Firefox and the toolbars but by chance the terminal was already open and I can input commands.

I'm unable to use gedit nano cat less, to view the log files. I'm not able to use, ubuntu-bug -p linux. Most if not all commands end like this
bash: /usr/bin/less: Input/output error

Very few that I know of give some information, most point to an I/O fault. Previous testing of hard drive for over 2 hours yielded no errors, similarly nothing in Smart. 

Output of dmesg
5932.861974 sd 0:0:0:0: [sda] Result hostbyte=DID_BAD_TARGET driverbyte=Driver_OK
5932.861983 sd 0:0:0:0: [sda] CDB Read(10)28 00 06 86 bc 00 00 08 00
5932.862013 end_request: I/O error,dev sda sector 109493432
5932.862064 sd 0:0:0:0: [sda] unhandled error code
 there are about 3 repeats of this, then another 4 with a different sector number. Repeating dmesg gives other sector numbers. Final line of dmesg is
[6066.692835] end_request: I/O error, dev sda sector 14706739

Output of mount
/dev/sda1 on /type ext4 (rw,errors=remount-ro,commit=0
next are several lines which I think are normal but the final lines are-
mount:warning /etc/mstab is not writeable (read only file system). Its possible that information reported by mount (8) is not up to date. For actual information about the system mount points check /proc/mounts file

Whilst it would be easy to suspect the hard drive all the tests I've done have been negative.

The frozen PC is upstairs with an open terminal. Can any useful information be acquired as to the cause of this problem? I know little about using bash.

Good luck there is a thread of 1000+ posts about 10.04 & random freezes with no real confirmed source,. It is going on with me & nothing is ever in the log file & I saw a post saying Ubuntu derivatives have this random freeze prob. It sounds like commands even give you error. Sorry about the rant & no help, but I am annoyed by this prob. If you can get a command through the terminal try sudo modprobe -r usbhid ; sudo modprobe usbhid, some one told me to try that.

---

### Post by Handssolow on 2010-10-19
Thanks for your reply.
I've briefly seen I/O error messages after a freeze when I've rebooted with Ctrl+Alt+Del. Mostly I've had to hard reset. I think it isn't a usb problem.
I've just found  Launchpad report of someone having an I/O message that wasn't hardware related but solved by using a different kernel.

[https://bugs.launchpad.net/ubuntu/+bug/366867](https://bugs.launchpad.net/ubuntu/+bug/366867)
Quote:bash: /usr/bin/gvim: Input/output error

---

### Post by CharlesA on 2010-10-19
I/O errors usually mean that it's having problems reading the hard drive. That would explain why it froze.

You might want to check out the SMART data of that drive.

---

### Post by WorMzy on 2010-10-19
Sounds to me like you've got bad sectors on your hard drive. Boot into a liveCD and run palimpsest. Click on sda and choose "SMART Data". It'll tell you if there are any bad sectors there. Also look down the list of Attributes and see if there's any "Bad" or "Failure" Assessments. If there are none, then run the Extended self-test just in case.

---

### Post by Handssolow on 2010-10-19
I've finally had to reboot the PC and I'm using it to post now. There's nothing in the logs for the few hours the PC froze, recordings stopped at about 12.30pm. I'll re-run the tests of memory and hard drive as I did when this first freezing started but I doubt it will show anything wrong.

---

### Post by utilitytrack on 2010-10-19
**Handssolow**

Put here output of
```
# smartctl -i --attributes /dev/sda
```

---

### Post by Handssolow on 2010-10-19
I ran the Samsung Hard utility HUTIL for 2 hours 12 minutes and it passed everything. smartctl gives this-

```
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint P120 series
Device Model:     SAMSUNG SP2504C
Serial Number:    S09QJ1PP411260
Firmware Version: VT100-50
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Tue Oct 19 20:48:45 2010 BST

==> WARNING: May need -F samsung3 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   253   253   025    Pre-fail  Always       -       5952
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       966
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3709
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       716
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   148   139   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   148   139   000    Old_age   Always       -       30
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1518074
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       59
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   100   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0032   085   085   000    Old_age   Always       -       5003
```

Palimpset says the hard drive is passing everything

So what's the verdict now? Is my faulty hard drive the likely cause of all the freezes I've been getting or might it not be faulty? The balance of probabilities suggests the hard drive isn't the cause?

---

### Post by WorMzy on 2010-10-19
The only other things I can think of that may cause this is a loose connector and/or a dodgy motherboard. Does your PC get moved about/knocked a lot?

---

### Post by CharlesA on 2010-10-19
> **Handssolow said:**
> I ran the Samsung Hard utility HUTIL for 2 hours 12 minutes and it passed everything. smartctl gives this-

```
smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint P120 series
Device Model:     SAMSUNG SP2504C
Serial Number:    S09QJ1PP411260
Firmware Version: VT100-50
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Tue Oct 19 20:48:45 2010 BST

==> WARNING: May need -F samsung3 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   253   253   025    Pre-fail  Always       -       5952
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       966
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3709
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       716
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   148   139   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   148   139   000    Old_age   Always       -       30
[COLOR="Blue"]195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1518074[/COLOR]
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
[COLOR="Blue"]199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       59[/COLOR]
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   100   000    Old_age   Always       -       0
[COLOR="Blue"]202 Data_Address_Mark_Errs  0x0032   085   085   000    Old_age   Always       -       5003[/COLOR]
```

Palimpset says the hard drive is passing everything

I've highlighted the things in blue that have me worried.

See [here]("http://en.wikipedia.org/wiki/S.M.A.R.T.#Known_ATA_S.M.A.R.T._attributes") for some explanation as to what some of the SMART reading mean.

Would be a good idea to reseat the data and power cable.

---

### Post by edward1978 on 2010-10-19
> **utilitytrack said:**
> **Handssolow**

Put here output of
```
# smartctl -i --attributes /dev/sda
```

Thats not working for me I get Permission denied or a list of commands.

---

### Post by CharlesA on 2010-10-19
> **edward1978 said:**
> Thats not working for me I get Permission denied or a list of commands.

Just put ***sudo*** before that command.

---

### Post by edward1978 on 2010-10-19
> **CharlesA said:**
> Just put ***sudo*** before that command.
:biggrin:

=== START OF INFORMATION SECTION ===
Device Model:     WL400GSA1672
Serial Number:    WOL240018242
Firmware Version: 12.06H12
User Capacity:    400,088,457,216 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 published, ANSI INCITS 397-2005
Local Time is:    Tue Oct 19 22:31:19 2010 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   232   220   021    Pre-fail  Always       -       5408
  4 Start_Stop_Count        0x0032   099   099   040    Old_age   Always       -       1611
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       3731
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1605
194 Temperature_Celsius     0x0022   116   091   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       189
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

Hmmm, maybe my drive is the culprit of the freezing.

---

### Post by CharlesA on 2010-10-19
Could be.

He's what the SMART status of one of my drives (the OS drive on my server):

```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD3200AAKS-00L9A0
Serial Number:    WD-WCAV20630592
Firmware Version: 01.03E01
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Oct 19 19:41:52 2010 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   132   131   021    Pre-fail  Always       -       4366
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       434
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       11604
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       414
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       92
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       434
194 Temperature_Celsius     0x0022   114   097   000    Old_age   Always       -       29
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       9
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
```

---

### Post by utilitytrack on 2010-10-20
> **Handssolow said:**
> smartctl gives this

```

smartctl 5.40 2010-03-16 r3077 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net
...
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       59
202 Data_Address_Mark_Errs  0x0032   085   085   000    Old_age   Always       -       5003
...

```

(from dmesg)
```
5932.861974 sd 0:0:0:0: [sda] Result hostbyte=DID_BAD_TARGET driverbyte=Driver_OK
5932.861983 sd 0:0:0:0: [sda] CDB Read(10)28 00 06 86 bc 00 00 08 00
5932.862013 end_request: I/O error,dev sda sector 109493432
5932.862064 sd 0:0:0:0: [sda] unhandled error code

```


I can advice you to backup all your data. It seems your hard disk (or controller) quickly fail.

---

### Post by AoSteve on 2010-10-20
Using the smart data, the drive has only been operational for about 155 days.   I have many that are over 3 years, but the Hardware_ECC_Recovered does worry me with such a LARGE number.  Specially with the thres and worst being 100.   

I may be wrong here, but I believe that's the HDD controller error recovery.  This could be a problem in MANY things however.   I'd pull all of the cables out and replug them to make sure the connections are great.   Also check the BIOS for incorrect settings.  I'd definitely start suspecting problems with the HDD or bios settings.

---

### Post by edward1978 on 2010-10-20
So is my drive gooing bad or is a cable loose? It did go with me on a move from Southern Illinios to Mid state, New York. I was in there to take out a bad drive after we got here though, Maybe this one is going to??

---

### Post by CharlesA on 2010-10-20
> **edward1978 said:**
> So is my drive gooing bad or is a cable loose? It did go with me on a move from Southern Illinios to Mid state, New York. I was in there to take out a bad drive after we got here though, Maybe this one is going to??

I'd reseat the cable first and see if the problem goes away. If not, replace the drive and then go from there.

---

### Post by coldraven on 2010-10-20
I don't trust SMART data. It has been showing a vast number of errors on this laptop from the day it was new. It still works!
See the screenshot:

---

### Post by CharlesA on 2010-10-20
> **coldraven said:**
> I don't trust SMART data. It has been showing a vast number of errors on this laptop from the day it was new. It still works!
See the screenshot:

That would be a bad reading. No piece of software is perfect on all equipment.

---

### Post by psusi on 2010-10-20
Looks like a bad or loose cable.  For some reason, the drive goes out to lunch as if it were unplugged.

---

### Post by utilitytrack on 2010-10-20
> **coldraven said:**
> I don't trust SMART data.

Very bad. Your hard drive, according to screenshot, has a lot of reallocated sectors. You should to worry about backup all data. Read this:

a) [http://sourceforge.net/mailarchive/forum.php?thread_name=B78676C11D549249AB29226D36F41406A85D91F5%40WOK-SRV-020.acalsupplychain.com&forum_name=smartmontools-support]("http://sourceforge.net/mailarchive/forum.php?thread_name=B78676C11D549249AB29226D36F41406A85D91F5%40WOK-SRV-020.acalsupplychain.com&forum_name=smartmontools-support")
b) [http://sourceforge.net/mailarchive/forum.php?thread_name=BLU0-SMTP9705A8EA0B1D09F608C095D8FA0%40phx.gbl&forum_name=smartmontools-support]("http://sourceforge.net/mailarchive/forum.php?thread_name=BLU0-SMTP9705A8EA0B1D09F608C095D8FA0%40phx.gbl&forum_name=smartmontools-support")
c) [http://sourceforge.net/mailarchive/forum.php?thread_name=l2o5da0588e1005081514y3dfd6ae7ra5e4bacb98183143%40mail.gmail.com&forum_name=smartmontools-support]("http://sourceforge.net/mailarchive/forum.php?thread_name=l2o5da0588e1005081514y3dfd6ae7ra5e4bacb98183143%40mail.gmail.com&forum_name=smartmontools-support")

---

### Post by CharlesA on 2010-10-20
In the case of coldraven's reading, it would be that the drive isn't playing nice with the SMART sensors. If they ran the software from the manufacturer, it would probably come up fine.

---

### Post by coldraven on 2010-10-21
CharlesA is correct. I ran the Hitachi test program which did not find any problems.
With that amount of errors this PC would have stopped working by now.

---

### Post by utilitytrack on 2010-10-21
> **CharlesA said:**
> ...it would be that the drive isn't playing nice with the SMART sensors.

It may be.

> [I]**Raw Values**
Please keep in mind that the conversion from RAW value to a quantity with physical units is not specified by the SMART standard!
smartctl only reports the different Attribute types, values, and thresholds as read from the device. It does not carry out the conversion between "Raw" and "Normalized" values: this is done by the disk's firmware.

In most cases, the values printed by smartctl are sensible. For example the temperature Attribute generally has its raw value equal to the temperature in Celsius.
However in some cases vendors use unusual conventions. For example the Hitachi disk on my laptop reports its power-on hours in minutes, not hours. Some IBM disks track three temperatures rather than one, in their raw values. Have a look at our wiki pages on topic SMART attributes. 
[**http://sourceforge.net/apps/trac/smartmontools/wiki/Howto_ReadSmartctlReports_ATA**]("http://sourceforge.net/apps/trac/smartmontools/wiki/Howto_ReadSmartctlReports_ATA")
[/I]

However, it's not mean that SMART data hasn't any sense.

PS
Here is interpretation of SMART Attributes for Hitachi devices: 
[http://sourceforge.net/apps/trac/smartmontools/wiki/AttributesIBM]("http://sourceforge.net/apps/trac/smartmontools/wiki/AttributesIBM")

---

### Post by CharlesA on 2010-10-21
> **coldraven said:**
> CharlesA is correct. I ran the Hitachi test program which did not find any problems.
With that amount of errors this PC would have stopped working by now.

Probably. When in doubt, you can run the manufacturer's utility and see if it spits back any errors.

> **utilitytrack said:**
> 
However, it's not mean that SMART data hasn't any sense.

That's true, I suppose.

I checked one of my Hitachi drives and it looked fine, but maybe it's the way it's hooked up since the one I checked is part of a RAID array.

---

### Post by Handssolow on 2010-10-21
I'm not sure what to do next, I'll see what happens. I've changed the SATA cable and moved it from the SATA11 socket to SATA. It's not so fast perhaps but the PC might be reliable and not freeze.

---

### Post by CharlesA on 2010-10-21
Best of luck. I hope everything works out for you.

---

### Post by edward1978 on 2010-10-27
> **CharlesA said:**
> I'd reseat the cable first and see if the problem goes away. If not, replace the drive and then go from there.

It barely freezes though, if it was a loose cable, it would give me trouble all the time right??

---

### Post by CharlesA on 2010-10-27
> **edward1978 said:**
> It barely freezes though, if it was a loose cable, it would give me trouble all the time right??

If it's not making a good connection, or the cable is bad, it would more then likely only happen intermittently, or not work at all.

---

### Post by WorMzy on 2010-10-27
> **edward1978 said:**
> It barely freezes though, if it was a loose cable, it would give me trouble all the time right??

Unfortunately, the same could be said for every other possible cause. When things randomly stop working for no apparent reason, it's difficult to know exactly what's causing it since it's almost impossible to deliberately reproduce. In these situations you may as well make sure that the hard-drive isn't failing, and that the cables are connected securely, if only to eliminate these as possible causes. You could also try reseating your RAM and make sure that your fans aren't clogged with dust.

---

### Post by edward1978 on 2010-10-27
> **WorMzy said:**
> Unfortunately, the same could be said for every other possible cause. When things randomly stop working for no apparent reason, it's difficult to know exactly what's causing it since it's almost impossible to deliberately reproduce. In these situations you may as well make sure that the hard-drive isn't failing, and that the cables are connected securely, if only to eliminate these as possible causes. You could also try reseating your RAM and make sure that your fans aren't clogged with dust.

Just put 2 sticks in a few months back, so everything should be ok, but I could look. Also I have Windows on the system, never noticed a prob. with it. Think I should download the Western Digital HDD tester & see what it says??

---

### Post by CharlesA on 2010-10-27
That would be a good idea.

Better safe then sorry and all that. :)

---

### Post by WorMzy on 2010-10-27
Did you have this problem a few months ago? ;)

I've never used the Western Digital HDD checker, so I could tell you whether it'll be of any user or not. Still, anything that might cast some light on the problem is worth trying.

---

### Post by Handssolow on 2010-10-27
Not much to report since I changed the Sata lead and moved from Sata11 to Sata as the PC hasn't been used much recently. When I have the time I intend to challenge the system by removing pci=noacpi which I added to Grub2. I've been busy with other work.

---

### Post by CharlesA on 2010-10-27
> **Handssolow said:**
> Not much to report since I changed the Sata lead and moved from Sata11 to Sata as the PC hasn't been used much recently. When I have the time I intend to challenge the system by removing pci=noacpi which I added to Grub2. I've been busy with other work.

How does that challenge the system?

---

### Post by edward1978 on 2010-10-28
> **CharlesA said:**
> That would be a good idea.

Better safe then sorry and all that. :)

I can't find my drive serial # at all when I enter it in the search box.

---

### Post by CharlesA on 2010-10-28
> **edward1978 said:**
> I can't find my drive serial # at all when I enter it in the search box.

Look it up by model, I've had the same thing happen with my WD OEM drives.

---

### Post by Handssolow on 2010-10-28
> **CharlesA said:**
> How does that challenge the system?

Without booting with pci=noacpi in Grub2 the PC freezes frequently, with it the freezes are far less frequent.
If I boot with noacpi I can't switch the PC off in the normal way.

---

### Post by CharlesA on 2010-10-28
> **Handssolow said:**
> Without booting with pci=noacpi in Grub2 the PC freezes frequently, with it the freezes are far less frequent.
If I boot with noacpi I can't switch the PC off in the normal way.

Wow that sucks. :(

---

