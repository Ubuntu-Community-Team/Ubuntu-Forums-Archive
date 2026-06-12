---
title: "Bad harddrive?"
date: 2011-09-26
forum: General Help
---

### Post by LuniTux on 2011-09-26
Hello,

The computer that is having this problem is an HP and is only about 2 years old. It came with windows XP but started looping on the login screen after about the first 6 months. I reformatted the computer and installed Ubuntu 9.10 since then but recently have been having problems booting. When I start the computer, it boots up as root and without a GUI.

```
root@computer:~# 
```

If I try ```
sudo service gdm start
``` I get an error about the X server. But if I run ```
fsck
``` and then run ```
sudo service gdm start
```, The GUI loads.

It seems to me that this is a harddrive error but I wanted to post to see if anyone else has any other ideas about what it could be.

Thanks,

---

### Post by collisionystm on 2011-09-26
How long has 9.10 been on your computer? 

I would say

1) Bad Harddrive
2) Are you overclocking? The frequency's can scramble data on your hard drive.

---

### Post by SlugSlug on 2011-09-26
whats the error?

---

### Post by seawolf167 on 2011-09-26
> **collisionystm said:**
> 1) Bad HarddriveHow do you connect a OS login issue to a bad hard drive?

> **collisionystm said:**
> 2) Are you overclocking? The frequency's can scramble data on your hard drive.Where did you get this information? This is completely false.

As for your issue, 9.10 has passed its [end of life ]("https://wiki.ubuntu.com/Releases")and is no longer supported. When did this problem start to occur?

What is the "error about the x server" you are getting when you try the commands you posted?

---

### Post by matt_symes on 2011-09-26
Hi

You can check your hard drives SMART status using Disc Utility (Most modern hard drives have it). 

You can also do it from the command line using ```
man smartctl
```You will have to install ```
sudo apt-get install smartmontools
```Kind regards

---

### Post by collisionystm on 2011-09-26
> **seawolf167 said:**
> How do you connect a OS login issue to a bad hard drive?

Where did you get this information? This is completely false.

As for your issue, 9.10 has passed its [end of life ]("https://wiki.ubuntu.com/Releases")and is no longer supported. When did this problem start to occur?

What is the "error about the x server" you are getting when you try the commands you posted?

It is not false lol. Atleast in my experience and several of my friends. Of course I have not overclocked in some years, but we used to have the problem of hard drive's completely hosing if you clocked your CPU to high. It comes from personal experience not some gibberish on the internet.

---

### Post by seawolf167 on 2011-09-26
> **collisionystm said:**
> It is not false lol. Atleast in my experience and several of my friends. Of course I have not overclocked in some years, but we used to have the problem of hard drive's completely hosing if you clocked your CPU to high. It comes from personal experience not some gibberish on the internet.

You'll need to cite sources or provide evidence - else everyone on [overclock.net ]("http://overclock.net/")is going to be in for a bumpy ride! I've been overclocking for *years* with no problems. This is like saying if you overclock a 2Ghz processor to 3 Ghz it'll "scramble" your hard drive, but at stock 3Ghz it won't? Lol! Frequency (1/sec) and magnetic storage do not interact like you think they do.

---

### Post by collisionystm on 2011-09-26
[http://www.overclockers.com/overclocking-basic-training/](http://www.overclockers.com/overclocking-basic-training/)
> Harddrives: High quality harddrives are worth there weight in gold to the overclocker. Extreme overclocking can cause data corruption and, in rare occasions, scramble your harddrive. Usually the drive is not permanently damaged and can be reformatted, but it&#8217;s a huge hassle if you don&#8217;t have your data backed up.

There is obviously no real way to prove it to you, but I guess you can just take my word that this happens? Like I said, real experience with this happening. Maybe you just never clocked your CPU high enough?

---

### Post by seawolf167 on 2011-09-26
that page is from 2001 - just as ssds have advanced considerably in the last 4 years, so have hard drives in the past 10 years. I would be willing to place money that your cpu will burn up, overheat, etc. wayyy before anything would ever happen to your hard drive. data corruption from incorrectly set ram timings, forced reboots, instable cpu settings such as wrong multipliers, frequencies, etc. is definitely a likely possibility, but this has nothing to do with the cpu frequency scrambling a drive.

---

### Post by SweetBearCub on 2011-09-26
It's just my opinion, so feel free to ignore it, but I think that running components intentionally beyond their factory rated maximums is just ASKING for trouble.

---

### Post by rbowen1 on 2011-09-26
Back to original problem of a questionable hard disk drive.  

I agree that the smart drive disk utility would be a good start.  I would also consider running fsck on the hard disk drive.     Here is a link to more info on fsck and the options.
[http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm](http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm)
 Just make sure you run it against a specific partition and not the entire hard disk or will get an error about the super block.

---

### Post by seawolf167 on 2011-09-27
We still haven't heard back from the OP - I am still interested to see what his "error about the x server" is, perhaps [hopefully] it is just something simple like a xserver-xorg configuration issue.

---

### Post by LuniTux on 2011-09-28
Hello again,

The computer seems to be ok since I ran **fsck** It has done this before a couple of months ago. I did not write down the error and it has not appeared again. The computer has never been overclocked either.

Here is the smartchk info:

```
=== START OF INFORMATION SECTION ===
Device Model:     ST3160318AS
Serial Number:    9VMFA8TL
Firmware Version: HP35
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Sep 28 10:34:39 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 617) seconds.
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
recommended polling time: 	 (  31) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   119   099   006    Pre-fail  Always       -       223716961
  3 Spin_Up_Time            0x0023   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       581
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       24
  7 Seek_Error_Rate         0x002f   069   060   030    Pre-fail  Always       -       9766883
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1838
 10 Spin_Retry_Count        0x0033   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       291
180 Unknown_Attribute       0x002b   100   100   000    Pre-fail  Always       -       386643182
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   096   000    Old_age   Always       -       22
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   067   053   045    Old_age   Always       -       33 (Lifetime Min/Max 23/33)
194 Temperature_Celsius     0x0022   033   047   000    Old_age   Always       -       33 (0 14 0 0)
195 Hardware_ECC_Recovered  0x003a   059   054   000    Old_age   Always       -       223716961
196 Reallocated_Event_Count 0x0032   100   100   036    Old_age   Always       -       24
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      70%         0         -

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

If I am reading this correctly I think it is saying the HDD is ok?

---

### Post by matt_symes on 2011-09-28
Hi

> If I am reading this correctly I think it is saying the HDD is ok?

Your SMART report is acceptable.

As fsck fixed the issue, it looks like it was file system corruption.

Kind regards

---

### Post by seawolf167 on 2011-09-28
Yes, it appears that your hard drive is just fine and any errors which once [may have] existed do so no longer.

---

### Post by LuniTux on 2011-10-05
OK

Thanks for the everyone! :)

---

### Post by seawolf167 on 2011-10-05
Good to hear back from you! If you are paranoid (also just as good practice), ensure you have some backups lying around *just incase* :P I recommend [Clonezilla ]("http://www.clonezilla.org")for full disk images but you have [many options]("https://help.ubuntu.com/community/BackupYourSystem").

---

