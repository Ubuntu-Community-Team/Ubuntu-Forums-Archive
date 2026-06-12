---
title: "Powerful laptop dreadfully slow. Should I format it?"
date: 2011-12-16
forum: General Help
---

### Post by Irishpolyglot on 2011-12-16
Hey forum! I have a Dell XPS M1730, specs here:
[http://reviews.cnet.com/4507-3121_7-32687269.html](http://reviews.cnet.com/4507-3121_7-32687269.html)
Gradually, more and more, it is getting slower and slower. It's ridiculous now - if I click "Places" and a directory it takes up to ten seconds to open that directory :(
Firefox takes ages to do anything - clicking a new tab also requires a 3 second wait before anything replies and after logging in after boot-up, there is a very long delay before I can use the computer to do anything.

How can I solve this? I'm thinking of starting over from scratch, installing the latest release (I currently have Ubuntu 10.04 - it took 20 seconds for the "About Ubuntu" page to come up) over a formatted computer. Or is there a less drastic option?

If I do go down this path, any tips on to back up as much as I can in terms of settings and applications, other than copy and paste to an external drive, or should I really build everything from the ground up a second time?

---

### Post by N00b-un-2 on 2011-12-16
I would grab a live CD of another release and boot into it to see if the problem persists.  The first thing that that comes to my mind is your SATA drivers or settings.  Check your SATA settings in BIOS, and if that's not culprit the SATA controller for your particular laptop may be poorly supported in your kernel.  But like I said, it's only a hunch

---

### Post by tears of the river on 2011-12-16
> **Irishpolyglot said:**
> Hey forum! I have a Dell XPS M1730, specs here:
[http://reviews.cnet.com/4507-3121_7-32687269.html](http://reviews.cnet.com/4507-3121_7-32687269.html)
Gradually, more and more, it is getting slower and slower. It's ridiculous now - if I click "Places" and a directory it takes up to ten seconds to open that directory :(
Firefox takes ages to do anything - clicking a new tab also requires a 3 second wait before anything replies and after logging in after boot-up, there is a very long delay before I can use the computer to do anything.

How can I solve this? I'm thinking of starting over from scratch, installing the latest release (I currently have Ubuntu 10.04 - it took 20 seconds for the "About Ubuntu" page to come up) over a formatted computer. Or is there a less drastic option?

If I do go down this path, any tips on to back up as much as I can in terms of settings and applications, other than copy and paste to an external drive, or should I really build everything from the ground up a second time?

was ubuntu always this slow on your laptop or did it get slow over time??

---

### Post by Irishpolyglot on 2011-12-16
Ubuntu has progressively got slower and slower. When I first installed it, it was lightening fast. That's why I feel playing around with the BIOS settings won't do much good.

---

### Post by coldraven on 2011-12-16
Try opening a terminal, make it fullscreen then type "top".
See if anything is hogging your processor or memory.
Then ask someone else how to remove it :)

---

### Post by rng on 2011-12-16
Try 'System Monitor' application in System>Administration. It will show you what processes are running and if any process is taking too much memory or cpu usage. 

Backing up data and reinstalling may be the last option.

---

### Post by Irishpolyglot on 2011-12-17
According to both 'top' and the system monitor, once I close Firefox there is nothing significant eating up system resources, and yet it still takes 10 seconds after I click "Desktop" for it to finally open.

---

### Post by sanderd17 on 2011-12-17
> **N00b-un-2 said:**
> I would grab a live CD of another release and boot into it to see if the problem persists.  The first thing that that comes to my mind is your SATA drivers or settings.  Check your SATA settings in BIOS, and if that's not culprit the SATA controller for your particular laptop may be poorly supported in your kernel.  But like I said, it's only a hunch

I was also thinking about a HDD issue.

Maybe a bad sector or so? Can you look at your HDD with gparted, it will notify you of most common problems.

---

### Post by grahammechanical on 2011-12-17
Why not create another partition and install Ubuntu into that new partition and if it runs lightning fast then you know it is not a hardware problem. 

Do you have a separate /home folder? If so, you can do a fresh install of / partition and format it. By not marking the /home partition for format you will not lose any of your data or settings.

But the new install may also run slow because the problem may be with all the hidden configuration files in dot ( . ) folders which are in your home folder.

If you do a lot of modifications and a lot of program installs and removals there can (in my opinion) be conflicts with these configuration files that slow down things as the OS and the applications try to resolve the conflicts. This is my opinion and why I consider doing a completely fresh install with a format of my /home partition from time to time. I am think of doing this when I go from 11.10 to 12.04 next spring.

If you have identified certain programs that are slow. Then you could try removing those programs one at a time and at the same time renaming their hidden dot ( . ) folders. A re-install of the program will re-create these folders. If the program then runs fast you have solved your problem. The configuration settings for that program will be in the renamed folder. You might try selectively coping them into the newly created folder.

Some programs will let you backup configuration settings.

Regards.

---

### Post by cortman on 2011-12-17
> **sanderd17 said:**
> I was also thinking about a HDD issue.

Maybe a bad sector or so? Can you look at your HDD with gparted, it will notify you of most common problems.

When my Toshiba laptop's HDD started to give out, I had much the same problem- SUPER slow at times, failed bootups... Check it out with GParted.

---

### Post by Irishpolyglot on 2011-12-17
Just ran GParted from a live CD to scan & fix the drive and it didn't find any issues, so that's not it...

---

### Post by 1clue on 2011-12-17
To me it sounds like you have a full partition.

Please post the output of **df -h** as run from a terminal.

It could also be that you've chosen to sort directories by something inconvenient, like size.  In that sort of case, the system needs to get information about everything in the directory, then sort it by the inconvenient metric, and then reorganize everything.  If you include folder sizes you can have a truly long wait after awhile.

---

### Post by kaar3l on 2011-12-17
Install smartmontools
```
sudo apt-get install smartmontools
```
Then check the hdd smart
```
sudo smartctl -a /dev/sda
```
Check reallocated sector count.

---

### Post by Irishpolyglot on 2011-12-21
@1clue Here is what I saw after calling that code:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             398G  333G   45G  89% /
none                  2.0G  392K  2.0G   1% /dev
none                  2.0G  200K  2.0G   1% /dev/shm
none                  2.0G  324K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sdb1             459G  198M  435G   1% /media/310c3f78-f292-4416-98ae-360e57238986
/dev/sdc1             932G  314G  619G  34% /media/TOSHIBA EXT

```

@kaar3l
I ran what you suggested and got this:
```
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000BEVT-75ZAT0
Serial Number:    WD-WXNZ08L49102
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Dec 21 15:56:55 2011 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (13560) seconds.
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
recommended polling time: 	 ( 158) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       804
  3 Spin_Up_Time            0x0027   183   173   021    Pre-fail  Always       -       1808
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2720
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       12804
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2718
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       802
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       4948
194 Temperature_Celsius     0x0022   111   090   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   083   083   000    Old_age   Always       -       12820
241 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       16632562251
242 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       12035252549

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12716         -
# 2  Short offline       Completed without error       00%     11215         -
# 3  Offline             Interrupted (host reset)      80%      3140         -
# 4  Short offline       Completed without error       00%         3         -
# 5  Short offline       Interrupted (host reset)      80%         2         -
# 6  Short offline       Completed without error       00%         1         -
# 7  Short offline       Interrupted (host reset)      80%         0         -

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

I may just go ahead and format and reinstall everything afresh. Am looking into backing up my stuff now, unless you have another suggestion from this info...

---

