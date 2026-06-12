---
title: "harddrive hdd continually being accessed and freezing 10.04"
date: 2011-05-31
forum: General Help
---

### Post by elricscripts on 2011-05-31
My Ubuntu 10.04 freezes continually when it starts accessing the HDD. I will be working normally, then when i switch windows, it will suddenly access the HDD and spin up for 4 to 7 mins. I can't access anything during this period. The processor is generally only 1-5% impacted during this. I think its accessing the swap.
 
I admit, it's an older computer with only 2gb of RAM. Wondering how to debug this and if I should install an older version of Ubuntu to fix the issue. I've tried three different harddrives, so i know it's not errors on the disk.

---

### Post by linuxinstalledfromhdd on 2011-05-31
When you check the Disk Utility, and read what the SMART Status says, what does it report the hard drive's status as? Good, Bad, etc?

---

### Post by elricscripts on 2011-05-31
The smart data reports that the disk is:  "Disk is healthy"
 
here's an fdisk on the HDD:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c442d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38246       39218     7815622+  82  Linux swap / Solaris
/dev/sda2   *           1       38245   307202931   83  Linux
/dev/sda3           39219       60801   173365447+   7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by linuxinstalledfromhdd on 2011-05-31
Ok, in Disk Utility click on SMART Data and run the self test, and let us know what it says. What do the assessments readout?

What I would do is monitor the log files to see if there is any processes that could be running at the time of spin up and locking up your system.

---

### Post by elricscripts on 2011-05-31
sorry for my naiveness, but what logs are those?
 
I ran the smart tools, but realized there are no logs from the graphic interface... installing smartmontools to get readout...

---

### Post by elricscripts on 2011-05-31
When installing smartmontools, it errored with not enough memory. With a little investigation, I realized my swap drive was pointing to the incorrect UUID (hence not being used). I fixed it by filling in the correct swap data (perhaps the source of the problem):
[[COLOR=#0068cf]https://help.ubuntu.com/community/SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")
gksudo gedit /etc/fstab
deleted incorrect swap data and inserted the line (without quotes): "/dev/sda1 none swap sw 0 0"
 
Then issued the commands:
sudo swapoff -a
sudo /sbin/mkswap /dev/sda1
sudo swapon -a

---

### Post by elricscripts on 2011-05-31
Here's the smart results:
 
```

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [[COLOR=#0068cf]http://smartmontools.sourceforge.net/[/COLOR]]("http://smartmontools.sourceforge.net/")
 
=== START OF INFORMATION SECTION ===
Device Model:     ST3500413AS
Serial Number:    Z2A022PE
Firmware Version: JC45
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue May 31 03:19:59 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
 
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
 
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
was completed without error.
Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
without error or no self-test has ever 
been run.
Total time to complete Offline 
data collection: ( 600) seconds.
Offline data collection
capabilities: (0x7b) SMART execute Offline immediate.
Auto Offline data collection on/off support.
Suspend Offline collection upon new
command.
Offline surface scan supported.
Self-test supported.
Conveyance Self-test supported.
Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
power-saving mode.
Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
General Purpose Logging supported.
Short self-test routine 
recommended polling time: (   1) minutes.
Extended self-test routine
recommended polling time: (  83) minutes.
Conveyance self-test routine
recommended polling time: (   2) minutes.
SCT capabilities:        (0x103f) SCT Status supported.
SCT Feature Control supported.
SCT Data Table supported.
 
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       29670456
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       11
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   064   060   030    Pre-fail  Always       -       2760930
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       293
10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       11
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       9
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   065   063   045    Old_age   Always       -       35 (Lifetime Min/Max 35/37)
194 Temperature_Celsius     0x0022   035   040   000    Old_age   Always       -       35 (0 25 0 0)
195 Hardware_ECC_Recovered  0x001a   042   028   000    Old_age   Always       -       29670456
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       101159364723011
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       598822659
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       3766386234
 
SMART Error Log Version: 1
No Errors Logged
 
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       293         -
# 2  Conveyance offline  Completed without error       00%       293         -
# 3  Short offline       Completed without error       00%       293         -
# 4  Extended offline    Interrupted (host reset)      00%       293         -
 
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

### Post by linuxinstalledfromhdd on 2011-05-31
Install htop and monitor your system until it occurs and take note of the process that is causing this. It would be the same as task manager in Windows, if that helps. 

sudo apt-get install htop

You should find it in Applications >> System Tools

---

### Post by elricscripts on 2011-05-31
I'll do that... thanks for the help!

---

### Post by dandnsmith on 2011-05-31
elricscripts: in case you need reassuring about amount of RAM, I'm currently using 1G, and have systems running happily on rather less than that.

---

