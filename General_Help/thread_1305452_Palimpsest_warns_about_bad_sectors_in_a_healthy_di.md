---
title: "Palimpsest warns about bad sectors in a healthy disk."
date: 2009-10-29
forum: General Help
---

### Post by oblador on 2009-10-29
Hi friends,

I installed Ubuntu 9.10 and Palimpsest warns about bad sectors in a healthy disk. What can be done in order to Palimpsest behave properly?

Thanks.

PS: i have absolutely no doubt that palimpsest is mistaken, because I ran dozens of tests on my disk and it's ok.

---

### Post by alphaniner on 2009-10-29
Nothing personal, but what kind of tests did you run?

---

### Post by oblador on 2009-10-29
i tested with the software provided by the manufacturer of the hard drive (samsung), for example.

---

### Post by alphaniner on 2009-10-29
Full surface scan?  If so, that's pretty definitive.

I actually came across another person in a similar situation.  He never reported back after I suggested testing with the manufacturer's software, but he said the drive had been working 100% before he tried to use Palimpsest.  Here's the [thread]("http://ubuntuforums.org/showthread.php?t=1302565").  He posted some screenies there, you can see if your issue is the same.  Nothing wrong with dropping him a PM I think.

Otherwise, have you looked into bug reports on launchpad or elsewhere?

---

### Post by oblador on 2009-10-29
yes, my hd is perfect!

look at what i've found:

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)
 
someone needs to do something about it.

the big problem about the free software is that no one is to blame for anything. no one has real responsibility.

thanks.

---

### Post by alphaniner on 2009-10-29
> **oblador said:**
> the big problem about the free software is that no one is to blame for anything. no one has real responsibility.

Yeah, there's definitely some truth to that.  Of course, with non-free software, you're SOL when those who are responsible refuse to take responsibility.

---

### Post by oblador on 2009-10-29
yes, but what can I do about palimpsest? is there any other software to help me about it?
will Ubuntu 9.10 create bad sectors on my hd?

---

### Post by alphaniner on 2009-10-30
I don't even know what all Palimpsest is used for, to be honest.  If you're just trying to partition and format, that can be done via the command line.  There's plenty of tutorials out there to help you learn, and plenty of people here who will help if you have trouble with anything specific.

Or, you can boot to an older LiveCD and use gParted.  Granted those are just workarounds, not solutions, but at least you have options.

And I don't think there's any risk of physical damage to your HDD.

---

### Post by germund on 2009-10-30
I also just installed 9.10 and got the bad sectors warning.  Just prior to installing it I had issues with 9.04 and checked things over pretty carefully.  After seeing this thread I'm pretty sure Palimpsest is in error.

---

### Post by Primefalcon on 2009-10-30
Had the same warning myself, since a lot of people are complaining about this at the moment and I know this is a new drive now, I just disabled this notification for now until this bug is fixed

---

### Post by dj-toonz on 2009-10-30
It's a bug as it was In fedora 11 aswell (where it came from)

---

### Post by cerpin on 2009-10-30
I'm getting that same error message.  Just now updated, didn't get any screens. I got scared and booted into XP. I haven't run a diagnostic yet, but I'm hoping its just an error. I don't wanna have to reinstall everything.

---

### Post by rey1321 on 2009-10-30
Same here!!!!
I got exactly the same little window every time I boot up my system, this is annoying, the little hard drive icon is still next to my speaker icon at the upper right hand corner of the screen.

any solution for this bug, cause i know my HD is ok.

---

### Post by Primefalcon on 2009-10-30
Also for those that need to do partitioning, just reinstall and use gparted

---

### Post by oblador on 2009-10-30
because of this bug I went back to ubuntu 8.10.

was it necessary? or could I go on using ubuntu 9.10 with this palimpsest bug? is this really just a palimpsest bug? or something worse?

---

### Post by kingofpain on 2009-10-31
> **oblador said:**
> because of this bug I went back to ubuntu 8.10.

was it necessary? or could I go on using ubuntu 9.10 with this palimpsest bug? is this really just a palimpsest bug? or something worse?

Dude, going back to 8.10 isn't going to repair your hard drive! This Palimpsest (or whatever is called) is a tool that just checks the state of your hard drive, it does nothing else to it. I don't know yet if this error report is a bug or if it really means that the HDD is having trouble, but, anyway, the problem is strictly related to Palimpsest!
If you're annoyed by this warning, you can disable it.
Open Palimpsest, select hard drive, go to detailed information and check the "do not show warning...".

---

### Post by oblador on 2009-10-31
ok, you're right! i came back to 9.10 again. but I do believe palimpsest has a bug or it's being too perfectionist, because it's the only tool that shows my hd has bad sectors.

thanks.

---

### Post by ac77 on 2009-10-31
Definitely a problem with palimpset. I had the same problem and so I ran a scan using SpinRite, just in case. No errors, hard drive is healthy.

---

### Post by spnkybnky on 2009-10-31
I just upgraded to 9.10 and got the same warning. I installed 9.10 on both my machines and get the same warning on both.  I thought it might be because I have a dual boot and it was reading the Windows partition as bad sectors.  The warning doesn't seem to bother the overall running of the computers. I am running the scan right now to see if the program re-checks the system if it won't turn off the warning. If it does, I'll let everyone know. It not, I'll wait for a fix like everyone else ....   

You can go to "system" and "disk utility" and turn off the warning if you want. I am sure it will be fixed  in short order .   

9.10 does run quite a bit faster.

---

### Post by bhuvi on 2009-10-31
guess i'm not alone with this warning [http://ubuntuforums.org/showthread.php?t=1307972]("http://ubuntuforums.org/showthread.php?t=1307972")

---

### Post by GaryLittlemore on 2009-10-31
I too have this problem, I've just turned it off warning about my disk for the time being until this is fixed.

---

### Post by orb242 on 2009-10-31
Just a bug....disable the warning....it will be fixed in a update later....

---

### Post by operations.kt on 2009-11-01
> **spnkybnky said:**
> I just upgraded to 9.10 and got the same warning. I installed 9.10 on both my machines and get the same warning on both.  I thought it might be because I have a dual boot and it was reading the Windows partition as bad sectors.  The warning doesn't seem to bother the overall running of the computers. I am running the scan right now to see if the program re-checks the system if it won't turn off the warning. If it does, I'll let everyone know. It not, I'll wait for a fix like everyone else ....   

You can go to "system" and "disk utility" and turn off the warning if you want. I am sure it will be fixed  in short order .   

9.10 does run quite a bit faster.

This, I believe. 

I have two dual boot systems. Our desktop is a WinXP - SP3 / Ubuntu 9.10. That system has 2 hard drives, and each operating system gets one drive. My work laptop is a Vista - SP2 and Ubuntu 9.10 setup with (of course) only one hard drive. That unit is also all of 5 days old (I just got it, ordered new direct from Dell). Prior to today I was running Ubuntu 9.04 on both. Today I upgraded them, and got this same error (ID 197) only on the laptop. 

I get the feeling that people with multiple systems on one hard drive are seeing this more than anyone else. Most of the messages I've read are all dual boot. 

Anyone running JUST Ubuntu getting the same message?

At any rate, due to the vast number of reports this week on this, I'm guessing that the Palimpsest program is overly sensitive to dual boot setups. I just un-installed it and put in a different program that does the same thing. No issues reported. 

I'm paranoid, so I'll be checking again with a third program to be sure, but I think this is a program bug. 

Oh, and as this is my first post here, hello all.

---

### Post by Sharpie1 on 2009-11-03
The disk utility reported many bad sectors on my dual boot system.. as soon as I upgraded to 9.10 and recommended that I back up and replace the disk. I panicked and bought a second hard drive.. but on closer inspection,  Palimpsest reports a value of 1099366403 sectors waiting to be remapped. I checked the drive with the Fujitsu disk Utility from the Ultimate Boot Disk... all fine. With chkdsk in Windows, all fine. So I will be backing up my data anyway but hold off on replacing the disk. And I have switched off the warning (in the "More information" section)

Sharpie1

---

### Post by lotharmat on 2009-11-03
I get the same problem on a Dual Boot system. Samsung's disk checking utility did a full test including a full surface scan and reported no errors at all.

Is this definitely a bug?

---

### Post by P4man on 2009-11-03
> **lotharmat said:**
> I get the same problem on a Dual Boot system. Samsung's disk checking utility did a full test including a full surface scan and reported no errors at all.

Is this definitely a bug?

It is definitely a bug **if** palimpsest reports a negative or very high number or relocated disks. Anything else afaik has not been shown to be the result of a bug. If samsung's tool reports no relocated sectors and palimpsests warns you about a (*reasonable*) number, then please let me know.

---

### Post by TheForumTroll on 2009-11-03
If those who get this bug haven't done so already please add any new info to launchpad and/or use the "Does this bug affect you?" link.

---

### Post by bpeyser on 2009-11-03
@P4man: I think you are being too conservative in your interpretation of the bug in palimpsest. I am almost certain that palimpsest is giving me a false positive on my HD, but the numbers are not extreme. I had the same issue when I was looking at Fedora 11, which also had palimpsest running. After that, I ran SpinRite, and did the full test. Fedora 11 kept telling me my disk was failing.

As I understand it, Karmic added palimpsest, while it was not included with jaunty. Now it's happening in karmic just as it did in Fedora 11. I am about to run a manufacturer's utility (Seagate for me) just to be sure. I will report back with the results.

Palimpsest currently reporting:
"Disk has many bad sectors"
5--Reallocated sector count--Warning--Value=208;Threshold=36
197--Current pending sector count--Warning--Value=134;Threshold=0

None of the others are assessed as "Warning." However, one value is crazy:
195--Hardware ECC recovered--N/A--Value=134731102;Threshold=0

These values seem quite reasonable for a failing drive, but I don't think mine is failing. All my data are backed up with Unison anyway just in case. Everyone should view this as a reminder to never trust your hardware! Even if palimpsest says your drive is healthy, you could lose data if they aren't backed up. Mine are on three drives in two locations: this one, plus a RAID 1 array.

-bpeyser

---

### Post by P4man on 2009-11-03
> **bpeyser said:**
> @P4man: I think you are being too conservative in your interpretation of the bug in palimpsest. I am almost certain that palimpsest is giving me a false positive on my HD, but the numbers are not extreme. I had the same issue when I was looking at Fedora 11, which also had palimpsest running. After that, I ran SpinRite, and did the full test.

AFAICT spinrite is not a smart monitoring tool. A read/write test will not produce errors.. yet. Please run another [smart monitor application ]("http://en.wikipedia.org/wiki/S.M.A.R.T.")(speedfan does it if you have windows) to confirm or deny the palimpsest readout.  So far I posted in at least 2 other threads were people *thought* it was a palimpsest bug despite reasonable values and all 2 were confirmed to be actually failing disks by other smart monitoring tools. If yours passes speedfan or similar it would be the first time I see it and I will become less conservative ;)

---

### Post by P4man on 2009-11-03
BTW this here:

> **bpeyser said:**
> 

None of the others are assessed as "Warning." However, one value is crazy:
195--Hardware ECC recovered--N/A--Value=134731102;Threshold=0



Is normal. The assessment is N/A, it means palimpsest is not using it. Probably the drive doesnt offer that information. I have similar useless results which are ignored by palimpsest and other smart tools.

---

### Post by oblador on 2009-11-03
well, I'm not quite sure about what's happening with palimpsest (I'm a lawyer, I don't know very much about computers), what I do know is that I ran several tests in many different programs and no error was reported.

---

### Post by bpeyser on 2009-11-03
@P4man:
True, SpinRite is much more than a S.M.A.R.T. monitoring tool, but it does read S.M.A.R.T. info and presents/uses it:
[SIZE=1][COLOR=black]
> Does SpinRite support hard drive SMART capability?[/COLOR][/SIZE][SIZE=1][COLOR=Black]  Yes. SpinRite supports SMART more completely and usefully than anything else ever has. Upon first use, SpinRite activates and enables a drive's disabled SMART subsystem. When SpinRite is not actively running on the drive, the "static" state of the drive's SMART data is displayed. When SpinRite is running on a drive, the drive's SMART data — both the standard SMART parameters and the more detailed SMART event counters — are continuously polled, monitored, and displayed. Much more useful information about the true health and robustness of a drive can be gained by monitoring the SMART system's feedback while the drive is under an actual workload. No other software has ever done this.
[/COLOR][/SIZE]([http://www.grc.com/sr/faq.htm](http://www.grc.com/sr/faq.htm))

I ran the Seagate utility on my drive, both the "short" and "long" versions and it reported no problem. I just looked at the S.M.A.R.T. data in SpinRite, and it listed S.M.A.R.T. as PASSED, but I think I may see where Palimpsest is disagreeing. They both listed the reallocated sector count at 208. SpinRite says there is a "Margin" of 59 for reallocated sectors. Palimpsest lists "Current pending sector count" as 134 with a "Threshold" of 0, while SpinRite listed "uncorrectable" as 134 with no info for "Margin." I'm really not sure what these values mean for the health 

So the counts may be correct, but I don't think that Palimpsest agrees with the S.M.A.R.T. system as to whether the counts are indicative of a problem. For me, Palimpsest reported a problem for my disk in the beginning of June, and I'm still running with no other trouble. I was concerned at the time and ran a level 2 and level 4 SpinRite test--which should have found any problems. I feel like if the manufacturer's utility, and especially SpinRite find it working fine, I don't believe it's about to fail. SpinRite is the king of hard disk utilities.

-bpeyser

---

### Post by P4man on 2009-11-04
Well, Im not an expert in smart, but a relocated sector count >0 should be cause for concern. If its has high as 208 then your drive is dying. 

134 in-correctable bad sectors, if thats right (and I think its not, king or no king) would definitely mean your drive is dying. H

Im sorry but from what I can tell, Id say palimpsest is right and you got a problem. I bet over time those numbers will go up and you'll start getting filesystem visible errors.

---

### Post by Mistril on 2009-11-04
Palimpsest seems like it's bugging on my laptop...it says I have one million plus bad sectors. Is that even possible?

Weird..

[IMG]http://ubuntu-virginia.ubuntuforums.org/attachment.php?attachmentid=134751&stc=1&d=1257375471[/IMG]

---

### Post by P4man on 2009-11-04
> **Mistril said:**
> Palimpsest seems like it's bugging on my laptop...it says I have one million plus bad sectors. Is that even possible?

Weird..


Its not possible, its a bug. Check the "dont warn me.." until this is sorted.

---

### Post by oblador on 2009-11-05
I wonder if this bug only happens when we use ext4 partitions.

---

### Post by spoon_ on 2009-11-05
You could also install GSmartControl (it's in the 9.10 repos) and see if that reports any problems.

---

### Post by cariboo on 2009-11-05
Palimpsest will report if you have bad sectors on your hard drive. Click the more information link and scroll down,the sections with errors will be red. See the screenshot.

As you can see my hard drive has 6 bad sectors, once it reaches the threshold of 36, the drive should be toast.

---

### Post by P4man on 2009-11-06
> I wonder if this bug only happens when we use ext4 partitions.

Almost certainly: no. Its based on smart info from the drive's firmware, it should give you the exact same results even if the drive is unpartitioned and unformatted.

> **cariboo907 said:**
> 

As you can see my hard drive has 6 bad sectors, once it reaches the threshold of 36, the drive should be toast.

As i understand it, 36 is were palimpsest will start warning and no longer say the drive is ok. 100 is were the real problems start as the drive can no longer relocate bad sectors to spare ones (yours has 100 spares it seems)

Then again, I wonder if hdd's can relocate any bad sectors without losing data. IOW Im not sure if those 6 bad sectors you have (which are now remapped) are guaranteed to still have correct data. if someone knows more about how a drive handles this Id be interested in learning.

---

### Post by Sadaiyappan on 2009-11-06
same thing is happening to me on my brand new Dell mini 10v which I put Karmic Koala on...  What should I do?  Just ignore it?

---

### Post by bpeyser on 2009-11-06
Well it certainly looks like there are problems with my drive, according to Palimpsest, SpinRite, and GSmartControl. However, I am not going to worry about it until the S.M.A.R.T. system reports a failure for those values. GSmartControl and SpinRite both see those values but also report that S.M.A.R.T. hasn't listed them as "failed" yet. Palimpsest doesn't care what S.M.A.R.T. thinks and decides on its own that the drive is failing. It's been "failing" by Palimpsest's definition for more than half a year at least, and still no real problems!

I'm just going to keep doing a full SpinRite test every few months and keep myself backed up to my RAID array, which is done automatically every hour whenever I'm on the internet. So in other words, exactly what I would do even if it was "healthy." At this point, I don't think Dell will send me a new drive just because Palimpsest says so. If the S.M.A.R.T. system says it's failing, I'll get it replaced. If I even have this machine when that finally happens.

-bpeyser

---

### Post by P4man on 2009-11-06
> **bpeyser said:**
>  It's been "failing" by Palimpsest's definition for more than half a year at least, and still no real problems!

-bpeyser

My understanding is that Smart doesnt conclude, it reports. Its the program that interprets the readouts and decides to report something as a problem or not. 

Now if your problem has existed for a year and half, *and the numbers are not increasing*, then I would suspect at some point you suffered a head crash (bumping the drive while it was active?) and you lost those 200 or whatever sectors, but its not due to mechanical or magnetic wear and its probably safe to keep using it. At least not less safe than any other drive. 

But Id still say palimpsest interpretation is quite reasonable and not a bug. So  I stand by my observation that only obviously incorrect readouts (negative and unrealistic high relocated sector counts) produce invalid warnings in palimpsest due to a bug. I have to yet to see an incorrect warning for anything else.

---

### Post by bpeyser on 2009-11-07
Come to think of it, my drive is also reporting the temperature was too high at some point in the past. I'm guessing that was after a tech came out to replace my motherboard and screwed up the heat sink install. Turns out you really do need to pay attention to the thermal compound when you remove/replace a heat sink. Who knew? Apparently not professional computer technicians--LOL! When I started using it the fan went max speed and stayed that way. Dell sent someone back out and he fixed it, but maybe the drive overheated when that was going on. I suppose that could have caused some sector reallocations. I wouldn't know, since I wasn't monitoring S.M.A.R.T. at the time.

-bpeyser

---

### Post by kkady32 on 2009-11-07
i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healthy'

---

### Post by P4man on 2009-11-07
> **kkady32 said:**
> i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healthy'

Do you still have the original palimpsest error report? You probably had a non zero "current pending sector count". IOW sectors which the drive identified as bad (can be read but not written reliably), but has not yet remapped because they contain data, and can be read. Running recovery tools like seatools or what you used will force the drive to remap the bad sector(s) and as long as you have less than 30 or 40? such such sectors remapped to internal spares, palimpsest will okay the drive. 

Keep an eye on that count though, if it goes up your drive is dying and tools like "HDDRegenerator: really cant perform magic tricks to revive a dead drive.

Put another way, had you just reformatted your drive, the same would probably have occurred, but it doesnt mean your drive is doing all that great. Time will tell...

---

### Post by kkady32 on 2009-11-08
Before to use HDDRegenerator i reinstall fresh Ubuntu 9.10 3 time and this error message was still,try with fsck and testdisk and error was still.After i download the ESTOOL from Samsung(my HDD is Samsung) and make test with,he reported LBA error,then i use Hiren's Boot CD and make another test,the same.Then use HDD Regenerator,first time to test and find this error and then make scan and repair and the results is:disk is healthy.

---

### Post by operations.kt on 2009-11-09
I still think this might be an issue with Windows / Ubuntu dual boot systems and the partitions of drives...  I still haven't heard if this happens to people with single boot systems too. 

Again, this is a brand new laptop. Palimpsest reports 131 bad sectors, (started at 129, down to 127, today is 131), as does the smartctl program. 

> 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM160HI
Serial Number:    S14QJD0S897175
Firmware Version: HH100-15
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Mon Nov  9 09:03:17 2009 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection:          (  54) seconds.
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
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  54) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2187
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       3147
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       87
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       38
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       55
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1
194 Temperature_Celsius     0x0022   106   085   000    Old_age   Always       -       44 (Lifetime Min/Max 18/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4912
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       131
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       225
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        35         -
# 2  Short offline       Completed without error       00%         0         -

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


I wonder if maybe this has to do with the Windows half still waiting on me to finish some updates, or if the partition maybe did something wrong. 

This laptop is a brand new Dell Inspiron 1515, less than a month old (delivered on Oct 28th). Samsung Drive. While it is still under warranty, I kinda need it for work. 

So, do we know if this is a bug (possible, as a LOT pf people are reporting this, and I can't see so many people with new computers having bad drives) or not?

---

### Post by P4man on 2009-11-09
> **operations.kt said:**
> I still think this might be an issue with Windows / Ubuntu dual boot systems and the partitions of drives...  I still haven't heard if this happens to people with single boot systems too. 

Again, this is a brand new laptop. Palimpsest reports 131 bad sectors, (started at 129, down to 127, today is 131), as does the smartctl program. 

Palimpsest gives a nice explanation of what the "current pending sector count" means and why it can go up or down; clearly with smartctl confirming the value there is little doubt this is an accurate reading, rather than a bug. The drive being new doesnt mean its flawless. In fact yours seems very much troublesome, did you see the "Offline_Uncorrectable" count?

> I wonder if maybe this has to do with the Windows half still waiting on me to finish some updates, or if the partition maybe did something wrong. 

Absolutely not. This is OS and filesystem independent. Its even filesystem invisible for the most part, this information is provided to you directly by the harddisk firmware (which has no concept of what OS you are using, nor filesystem much less the state of your OS updates). This is hardware monitoring, not a software issue.

> This laptop is a brand new Dell Inspiron 1515, less than a month old (delivered on Oct 28th). Samsung Drive. While it is still under warranty, I kinda need it for work. 


Contact Dell for a replacement then..
> 
So, do we know if this is a bug (possible, as a LOT pf people are reporting this, and I can't see so many people with new computers having bad drives) or not?

I think a lot of people are only now discovering its not always software thats to blame for their problems. Although there are bugs in palimpsest giving false positives (actually heh negatives), which seems to confuse many people into thinking any warning by palimpsest is bogus, but yours isnt. You got a bad drive.

---

### Post by operations.kt on 2009-11-10
Ok, brand new drive. Installed Ubuntu 9.04 with the Vista Dual Boot. Rand smartctl again. 

Resutls:

> 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     FUJITSU MJA2160BH G2
Serial Number:    K950T9A28G0A
Firmware Version: 00850019
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3f
Local Time is:    Tue Nov 10 21:50:42 2009 EST
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
data collection:          ( 508) seconds.
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
recommended polling time:      (  72) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       69253
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       9019431321600
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       431
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       8
191 G-Sense_Error_Rate      0x0012   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       3
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       53
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       39 (Lifetime Min/Max 22/42)
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       176867
200 Multi_Zone_Error_Rate   0x0032   100   100   000    Old_age   Always       -       424843
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       399
241 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       125977030033409
242 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       36980155613186

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


Am I wrong, or is that actually WORSE? Did I really get two bum drives from Dell in a row?

---

### Post by P4man on 2009-11-11
that seems so bad I cant believe it lol. Especially this one:
5 Reallocated_Sector_Ct 0x0033 100 100 024 Pre-fail Always - 9019431321600

That is what palimpsest reports on many fujitsu drives and is generally believed to be a bug in palimpsest but now im wondering if it has to do with how fujitsu drives report smart values. If it were just that Id dismiss without thinking twice but then you also have high raw read errors and udma crc errors.

Could you run a windows based smart monitoring utility? Speedfan is one, but there are a ton.

---

### Post by operations.kt on 2009-11-11
Yeah, I'll swap boot into Vista and try out SpeedFan, and let you know.

---

### Post by operations.kt on 2009-11-11
Ok, speedfan would not recognize the drive, so using this;

 [http://en.wikipedia.org/wiki/Comparison_of_S.M.A.R.T._tools](http://en.wikipedia.org/wiki/Comparison_of_S.M.A.R.T._tools)

I went with Hard Disk Sentinel. Those results are as follows (only the HD stuff, it reports on everything, including your virtual memory)-

> 
    Serial ATA Features
   ---------------------
    S-ATA Compliance . . . . . . . . . . . . . . . . : Yes
    S-ATA I Signaling Speed (1.5 Gps)  . . . . . . . : Supported
    S-ATA II Signaling Speed (3 Gps) . . . . . . . . : Supported
    S-ATA Gen3 Signaling Speed (6 Gps) . . . . . . . : Not supported
    Receipt Of Power Management Requests From Host . : Supported
    PHY Event Counters . . . . . . . . . . . . . . . : Supported
    Non-Zero Buffer Offsets In DMA Setup FIS . . . . : Not supported
    DMA Setup Auto-Activate Optimization . . . . . . : Supported, Disabled
    Device Initiating Interface Power Management . . : Supported, Disabled
    In-Order Data Delivery . . . . . . . . . . . . . : Not supported
    Asynchronous Notification  . . . . . . . . . . . : Not supported
    Software Settings Preservation . . . . . . . . . : Supported, Enabled
    Native Command Queuing (NCQ) . . . . . . . . . . : Supported
    Queue Length . . . . . . . . . . . . . . . . . . : 32

    Disk Information
   ------------------
    Form Factor  . . . . . . . . . . . . . . . . . . : 2.5" 
    Capacity . . . . . . . . . . . . . . . . . . . . : 160 GB (160 x 1,000,000,000 bytes)
    Number Of Disks  . . . . . . . . . . . . . . . . : 1
    Number Of Heads  . . . . . . . . . . . . . . . . : 2
    Rotational Speed . . . . . . . . . . . . . . . . : 5400 RPM
    Rotation Time  . . . . . . . . . . . . . . . . . : 11.11 ms
    Average Rotational Latency . . . . . . . . . . . : 5.56 ms
    Disk Interface . . . . . . . . . . . . . . . . . : Serial-ATA/300
    Buffer-Host Max. Rate  . . . . . . . . . . . . . : 300 MB/seconds
    Buffer Size  . . . . . . . . . . . . . . . . . . : 8192 KB
    Drive Ready Time (Typical) . . . . . . . . . . . : ? seconds
    Average Seek Time  . . . . . . . . . . . . . . . : 12.0 ms
    Track To Track Seek Time . . . . . . . . . . . . : 1.5 ms
    Full Stroke Seek Time  . . . . . . . . . . . . . : 22.0 ms
    Width  . . . . . . . . . . . . . . . . . . . . . : 70.0 mm (2.8 inch)
    Depth  . . . . . . . . . . . . . . . . . . . . . : 100.0 mm (3.9 inch)
    Height . . . . . . . . . . . . . . . . . . . . . : 9.5 mm (0.4 inch)
    Weight . . . . . . . . . . . . . . . . . . . . . : 101 grams (0.2 pounds)
    Acoustic (Idle)  . . . . . . . . . . . . . . . . : 2.5 Bel
    Required Power For Spinup  . . . . . . . . . . . : 1,100 mA
    Power Required (Seek)  . . . . . . . . . . . . . : 2.1 W
    Power Required (Idle)  . . . . . . . . . . . . . : 0.8 W
    Power Required (Standby) . . . . . . . . . . . . : 0.1 W
    Manufacturer . . . . . . . . . . . . . . . . . . : Fujitsu Computer Products of America, Inc.
    Manufacturer Website . . . . . . . . . . . . . . : [http://www.fcpa.fujitsu.com/products/hard-drives](http://www.fcpa.fujitsu.com/products/hard-drives)

    S.M.A.R.T.
   ------------
No.  Attribute                Thre.. Value  Worst  Data                Status                   Flags                                                  
1    Raw Read Error Rate      46     100    100    00000003EBDC        OK                       Error-Rate, Performance, Statistical, Critical         
3    Spin Up Time             25     100    100    000000000000        OK                       Statistical, Critical                                  
5    Reallocated Sectors Co.. 24     100    100    083400000000        OK                       Self Preserving, Event Count, Statistical, Critical    
9    Power On Time Count      0      100    100    000000000237        OK (Always passing)      Self Preserving, Event Count, Statistical              
12   Drive Power Cycle Count  0      100    100    000000000009        OK (Always passing)      Self Preserving, Event Count, Statistical              
191  G-Sense Error Rate       0      100    100    000000000001        OK (Always passing)      Event Count, Statistical                               
192  Power off Retract Cycle  0      100    100    000000000003        OK (Always passing)      Self Preserving, Event Count, Statistical              
193  Load/Unload Cycle Count  0      100    100    000000000036        OK (Always passing)      Self Preserving, Event Count, Statistical              
194  Disk Temperature         0      100    100    002A00140024        OK (Always passing)      Self Preserving, Statistical                           
199  Ultra ATA CRC Error Co.. 0      100    100    00000002F910        OK (Always passing)      Self Preserving, Event Count, Statistical              
200  Write Error Rate         0      100    100    000000070988        OK (Always passing)      Self Preserving, Event Count, Statistical              
240  Head Flying Hours        0      100    100    000000000218        OK (Always passing)      Self Preserving, Event Count, Statistical              
241  Vendor-specific          0      100    100    763CF1800001        OK (Always passing)      Self Preserving, Event Count, Statistical              
242  Vendor-specific          0      100    100    259FD7B80002        OK (Always passing)      Self Preserving, Event Count, Statistical              

    Transfer Rate Information
   ---------------------------
    Total Data Read  . . . . . . . . . . . . . . . . : 317 MB,  317 MB since installation  (11/11/2009)
    Total Data Write . . . . . . . . . . . . . . . . : 12 MB,  12 MB since installation
    Average Reads Per Day  . . . . . . . . . . . . . : 317.00 MB
    Average Writes Per Day . . . . . . . . . . . . . : 12.00 MB
    Current Transfer Rate  . . . . . . . . . . . . . : 506 KB/s
    Maximum Transfer Rate  . . . . . . . . . . . . . : 39060 KB/s
    Current Read Rate  . . . . . . . . . . . . . . . : 255 KB/s
    Current Write Rate . . . . . . . . . . . . . . . : 250 KB/s
    Current Disk Usage . . . . . . . . . . . . . . . : 5 %



It reported 1, 3 and 5 as errors. So yeah, I got another POS drive from Dell. I'm about to send the whole thing back, get a refund, and just get some cheap laptop from Walmart. This is stupid.

---

### Post by P4man on 2009-11-11
seems rather unlikely to receive 2 bad drives in a row, unless Dell makes a habit of sending previously returned drives back to other customers. Its clearly not a software bug though, so if its not Dell trying to sucker you into a bad drive, I wonder if its something with the machine itself.

---

### Post by operations.kt on 2009-11-12
Also a thought I had before I came back here. Something about the config being mean to drives or something, or maybe something else in the hardware causing false positives. 

Either way is a bad thing. 

So, I called Dell, invoked my '21 day' full refund option, and as of right now UPS is returning the thing to Tennessee for me, at Dell's cost. In the end, the only things I am out is time and the initial $7 shipping, which when you think about it, $7 is cheap to rent a laptop for about 2 weeks... 

When my refund is processed, I'll think about a different unit. I have options, and time to research for one that works good as a dual boot setup. 

Thanks for your help.

---

### Post by lavinog on 2009-11-12
> **cariboo907 said:**
> Palimpsest will report if you have bad sectors on your hard drive. Click the more information link and scroll down,the sections with errors will be red. See the screenshot.

As you can see my hard drive has 6 bad sectors, once it reaches the threshold of 36, the drive should be toast.

Normally with SMART when the normalized value falls below the threshold, your drive has a statistically higher chance of failing.

In this case the reallocated sector count threshold is based on the number of sectors reserved for reallocation of data from sectors that might be bad.
some manufacturers normalize this value to 100 and some to a value >200...yours looks like 100 which likely means that those 36 sectors make up less than 1% of the total reserve.

All of the reallocation happens within the drives firmware...the os has nothing to do with it.

Also SMART is based on statistics (most likely on RMA'd drives and lab tests)  Your drive can always fail with out exceeding any SMART limits, or your drive can exceed the limits for years without ever dying.

Best advice:  Always keep up with backups, and don't stress out about these warnings.

---

### Post by jasonadiehl on 2009-11-14
Quote:
*********************************
Anyone running JUST Ubuntu getting the same message?
*****************************

Hello all,

I am running only Ubuntu and I get the same error.

---

### Post by operations.kt on 2009-11-14
Thank you. It's only one, but helps toward it being hardware issues and not me botching a dual boot setup twice in a row. Which makes me feel a bit better. 

If you're still looking P4, have you heard any news (good or bad) on the Acer Aspire AS5517 laptop running Ubuntu? They have a real good price on them here locally, and I like the specs. Gotta admit, having a numeric keypad on a laptop would be nice too. I'm considering it for a replacement.

---

### Post by P4man on 2009-11-15
> **operations.kt said:**
> Thank you. It's only one, but helps toward it being hardware issues and not me botching a dual boot setup twice in a row. Which makes me feel a bit better. 

If you're still looking P4, have you heard any news (good or bad) on the Acer Aspire AS5517 laptop running Ubuntu? They have a real good price on them here locally, and I like the specs. Gotta admit, having a numeric keypad on a laptop would be nice too. I'm considering it for a replacement.

No and google doesnt reveal a lot either, but ive read a few drama stories with other acer aspire's, and I got one myself which Im not too thrilled about, although mine does work fine with ubuntu now,  it has been problematic until jaunty. Issues with buggy bios giving all sorts of problems with suspend, audio, sata.. Then again who knows if that will apply with a very different one...

If the shop lets you, try booting it from a livecd so you can test a few things at least.

---

### Post by bendib on 2009-11-16
My Acer Aspire One reports a total of 354 bad sectors, but it still performs just fine. I rarely keep the same distro on there, and have used dd if=/dev/zero of=/dev/sda on it several times when installing new distros. No errors. I did notice, however, when it fell off the couch arm, about a 1 and 2/3 foot drop, the count went up one. Oh well. BTW: I use Fedora 11 most of the time.

---

### Post by dcstar on 2009-11-21
> **P4man said:**
> that seems so bad I cant believe it lol. Especially this one:
5 Reallocated_Sector_Ct 0x0033 100 100 024 Pre-fail Always - 9019431321600

That is what palimpsest reports on many fujitsu drives and is generally believed to be a bug in palimpsest but now im wondering if it has to do with how fujitsu drives report smart values. If it were just that Id dismiss without thinking twice but then you also have high raw read errors and udma crc errors.


It is quite possible that the SMART data format for some drives is not being parsed correctly, all palimpsest seems to do is use the data from the underlying libatasmart library package.

---

### Post by Rich_S on 2009-11-22
I just upgraded my main PC from Ubuntu 9.04 to 9.10 today.

Palimpsest is reporting Disk Has Many Bad Sectors.

Drive in question is a Seagate Barracuda 7200 RPM SATA 500GB - ST3500630AS.

A little searching revealed some known bugs with Palimpsest. So I installed smartmontools.

Output of tests is below:

> 
----------------------------------------------
rich@rich-desktop:~$ sudo smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num Test_Description Status Remaining LifeTime(hours) LBA_of_first_error
# 1 Extended offline Completed without error 00% 17406 -
# 2 Short offline Completed without error 00% 17403 -




rich@rich-desktop:~$ sudo smartctl -l error /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
No Errors Logged



rich@rich-desktop:~$ sudo smartctl -A /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_FAILED RAW_VALUE
1 Raw_Read_Error_Rate 0x000f 117 094 006 Pre-fail Always - 159933204
3 Spin_Up_Time 0x0003 094 093 000 Pre-fail Always - 0
4 Start_Stop_Count 0x0032 100 100 020 Old_age Always - 97
5 Reallocated_Sector_Ct 0x0033 100 100 036 Pre-fail Always - 0
7 Seek_Error_Rate 0x000f 083 060 030 Pre-fail Always - 201963397
9 Power_On_Hours 0x0032 081 081 000 Old_age Always - 17406
10 Spin_Retry_Count 0x0013 100 100 097 Pre-fail Always - 0
12 Power_Cycle_Count 0x0032 099 099 020 Old_age Always - 1248
187 Reported_Uncorrect 0x0032 100 100 000 Old_age Always - 0
189 High_Fly_Writes 0x003a 100 100 000 Old_age Always - 0
190 Airflow_Temperature_Cel 0x0022 055 046 045 Old_age Always - 45 (Lifetime Min/Max 31/49)
194 Temperature_Celsius 0x0022 045 054 000 Old_age Always - 45 (0 22 0 0)
195 Hardware_ECC_Recovered 0x001a 055 051 000 Old_age Always - 194793134
197 Current_Pending_Sector 0x0012 001 001 000 Old_age Always - 4294967295
198 Offline_Uncorrectable 0x0010 001 001 000 Old_age Offline - 4294967295
199 UDMA_CRC_Error_Count 0x003e 200 200 000 Old_age Always - 0
200 Multi_Zone_Error_Rate 0x0000 100 253 000 Old_age Offline - 0
202 TA_Increase_Count 0x0032 100 253 000 Old_age Always - 0
-------------------------


The Current_Pending_Sector and Offline_Unrecoverable raw values really have me worried.

Here's what's bugging me:

How can LBA_of_first_error be - (nothing) when there are 4294967295 Offline_Uncorrectable sectors?

So then I downloaded the Seagate Seatools Disk Diagnostic Utilities and created a bootable CD.

Ran the short version and long version and both reported: "SMART Is Supported And ENABLED. SMART Has NOT Been Tripped. No Errors Found".

Please help.  Is my disk about to die or is this a false positive?

---

### Post by jeb800e on 2009-11-22
:.deleted:.

---

### Post by P4man on 2009-11-22
> **Rich_S said:**
> I 

Please help.  Is my disk about to die or is this a false positive?

Looks like a false positive to me. Those numbers are way too high to be credible. I think smartmontools and palimpsest rely on the libs though, can you try another windows based smart monitoring tool? Or something like ultimate boot cd?

---

### Post by lavinog on 2009-11-22
> **Rich_S said:**
> I just upgraded my main PC from Ubuntu 9.04 to 9.10 today.

Palimpsest is reporting Disk Has Many Bad Sectors.

Drive in question is a Seagate Barracuda 7200 RPM SATA 500GB - ST3500630AS.

What firmware does that drive have.
Some of those drives had a bad firmware that causes the drive to eventually stop working.

---

### Post by jeb800e on 2009-11-22
[http://ubuntuforums.org/showthread.php?p=8367962#post8367962](http://ubuntuforums.org/showthread.php?p=8367962#post8367962)

---

### Post by dcstar on 2009-11-22
> **Rich_S said:**
> 
.........
**How can LBA_of_first_error be - (nothing) when there are 4294967295 Offline_Uncorrectable sectors?**
......
Please help.  Is my disk about to die or is this a false positive?

Because the underlying code that parses the SMART data is not doing its job properly - and all the utilities that rely on correct data are reporting incorrect results.

Since smartmontools and Palimpsest seem to use two different methods of collecting SMART data, if they are both reporting incorrect results then perhaps they are just not compatible with the SMART data from certain disk drives?

Anyway, this should be a Launchpad bug - people have reported it, haven't they?

---

### Post by lavinog on 2009-11-23
The problem with SMART is that there is no standard.  Each manufacture reports things differently.

If you had two of the same drives and one reported a problem, then you should backup your data...but then again, always backup your data, because a drive can easily fail without a SMART warning.

---

### Post by spaceriqui on 2009-12-03
I had a dual boot system as well on an hp mini 1037 (SAMSUNG HS06THB HD) and started getting this message when I upgraded.  It is not because it was a dual boot system thought, because it did it without windows (fresh install of Ubuntu OS on whole HD).

I did run the hard disk test in the BIOS and it failed that as well.  I was told to return to HP since it was under warranty, but all they did was reinstall windows and not replace the disk.  As soon as I got it back I noticed the same error 'reallocated sector count' ID=5 with the same 141 sectors.

Right now I am trying to get HP to replace it, although it now passes the BIOS tests.  Maybe it is not a big deal, and the disk could last a few years.  But I rather not take the risk.

---

### Post by lavinog on 2009-12-04
> **spaceriqui said:**
> 
I did run the hard disk test in the BIOS and it failed that as well.  I was told to return to HP since it was under warranty, but all they did was reinstall windows and not replace the disk.  As soon as I got it back I noticed the same error 'reallocated sector count' ID=5 with the same 141 sectors.


Do you know what the BIOS disk test failed it for?

---

### Post by davidsanchezvasquez on 2009-12-30
Hello,

New here in Ubuntu, and being an Ubuntu user since about 2 months ago. I'm glad so far, but just some minutes ago I updated to 9.10 (from 9.04) and I also experiencing the same warning message, Palimpsest is reporting Disk Has Many Bad Sectors.

Does anyone knows if this bug have been corrected? What's the solution for now? Just disable the warning message?

Cheers

---

### Post by lavinog on 2009-12-30
> **davidsanchezvasquez said:**
> Hello,

New here in Ubuntu, and being an Ubuntu user since about 2 months ago. I'm glad so far, but just some minutes ago I updated to 9.10 (from 9.04) and I also experiencing the same warning message, Palimpsest is reporting Disk Has Many Bad Sectors.

Does anyone knows if this bug have been corrected? What's the solution for now? Just disable the warning message?

Cheers

How old is your drive?
The warning is just a warning.  Your drive could fail soon, or it could fail in 5 years.  Either way, make sure you have a backup plan.
You could just disable the warning message since it wont do you much good anymore.
Also, I recently lost a harddrive.  I got the warning at the moment it died. So it isn't much of a early warning system.
The harddrive is about a year old, so that should tell you that a hard drive can die at any moment.  Also it was my backup storage drive...so make sure you have a backup for the backup.

---

### Post by Guilden_NL on 2010-01-01
Known bug with Palimpsest.  Main contributor is with Red Hat.

Not trying to point fingers here, but Canonical should yank it from the distro and shouldn't have included it with 9.10 given the bug reporting prior to release of 9.10.  I am scratching my head as to why they include apps that have widely known problems, yet they are very late in releasing apps that have been out for a while prior to Ubuntu release; e.g., Firefox.

Ah well, the latter question isn't nearly important as to why they include apps that are known to have problems.

---

### Post by Herman on 2010-03-12
:D But I happen to  LIKE   Palimpsest Disk Utility.

One of the reasons why it's good that everyone has it is because a lot of people install Ubuntu in computers that are getting old.
I think people should install Ubuntu in new computers, but that's just me. Not everyone think the same as me, and many times they install in old worn out hard disks and then come here to Ubuntu Web Forums wondering what's wrong with Ubuntu and why it doesn't work for them. On quite a large number of occasions, problems have been traced back to faulty hardware.

Volunteers who help in Ubuntu Web Forums give up their time to help Ubuntu for free.
Just because we're volunteers doing it for free doesn't mean our time is not valuable. 

I think that  Palimpsest Disk Utility is probably (generally) doing a good job of reporting the S.M.A.R.T. information from the hard disk. 
The problem is that too many people think the S.M.A.R.T. information in the hard disk is accurate and infallible.
I don't think it's wise to assume the S.M.A.R.T. info is accurate because hard disk drive manufacturers don't want to share their secret details with their competitors. The hard disk drive manufacturers deliberately obscure the data and they have their own proprietary programs for reading it their own secret way.
Therefore, I think we should take Palimpsest Disk Utility's with a grain of salt.

I still think Palimpsest Disk Utility is very useful, but a bad report should be interpreted as 'further testing required', not necessarily as an impending hard drive failure.
I wouldn't like to see it dropped from Ubuntu.

---

### Post by lavinog on 2010-03-13
> **Herman said:**
> :D But I happen to  LIKE   Palimpsest Disk Utility.

One of the reasons why it's good that everyone has it is because a lot of people install Ubuntu in computers that are getting old.
I think people should install Ubuntu in new computers, but that's just me. Not everyone think the same as me, and many times they install in old worn out hard disks and then come here to Ubuntu Web Forums wondering what's wrong with Ubuntu and why it doesn't work for them. On quite a large number of occasions, problems have been traced back to faulty hardware.

Volunteers who help in Ubuntu Web Forums give up their time to help Ubuntu for free.
Just because we're volunteers doing it for free doesn't mean our time is not valuable. 

I think that  Palimpsest Disk Utility is probably (generally) doing a good job of reporting the S.M.A.R.T. information from the hard disk. 
The problem is that too many people think the S.M.A.R.T. information in the hard disk is accurate and infallible.
I don't think it's wise to assume the S.M.A.R.T. info is accurate because hard disk drive manufacturers don't want to share their secret details with their competitors. The hard disk drive manufacturers deliberately obscure the data and they have their own proprietary programs for reading it their own secret way.
Therefore, I think we should take Palimpsest Disk Utility's with a grain of salt.

I still think Palimpsest Disk Utility is very useful, but a bad report should be interpreted as 'further testing required', not necessarily as an impending hard drive failure.
I wouldn't like to see it dropped from Ubuntu.

Well said.

Many users are switching to ubuntu because their systems can't run vista, and they don't want to run xp anymore.  I find it awkward when a user complains that their 10 year old video card cant handle desktop effects, or their 15 year old cdrom drive cant read a cd correctly and they blame it all on ubuntu.

I tried out Lucid alpha today and the changes to palimpsest are impressive.
I of course got the same warning, and 6 months later I still have the same relocated sector count.  For all I know, I got these relocated sectors from using windows 4 years ago, or from improperly using a dd command...because palimpset didn't exist prior to karmic, I will never know when it occurred, so I can not blame Ubuntu.

Arstechnica has a good article on the issues of error correction in new drives: [http://arstechnica.com/microsoft/news/2010/03/why-new-hard-disks-might-not-be-much-fun-for-xp-users.ars](http://arstechnica.com/microsoft/news/2010/03/why-new-hard-disks-might-not-be-much-fun-for-xp-users.ars)
> 
We all like to think of hard disks as neatly storing the 1s and 0s that make up our data and then reading them back with perfect accuracy, but unfortunately the reality is nothing like as neat.


---

### Post by HC48 on 2010-03-19
Hello,
I have had the scary Palimpset message for 2 days on a 'passed on' computer which originally had windows XP, then Ubuntu + windows XP. When I got it last year I got Ubuntu 9.4 installed alone, everything was great, then I got Ubuntu 9.10 for Christmas :).  I'm a little disappointed with 9.10 as my scanner hasn't worked since I updated and now I have this Drive message. It seems to be a little slower sometimes too. I realize my computer may be getting tired but the original owner says it shouldn't yet.
I am still a beginner and most things on my computer are done by someone else.
For others having multifunctional scanner problems see my message:
[http://ubuntuforums.org/showthread.php?p=8898867#post8898867](http://ubuntuforums.org/showthread.php?p=8898867#post8898867)
... and in case any of you experts can help ):P

Thank you,

H :)

22 March: decided to buy new HD

---

### Post by HC48 on 2010-04-09
9th April: computer still working, the warning message increases by a sector every other startup. Value = 71 for the moment. (Limit is supposed to be 63)
H :)

PS I have backed up of course but I'm curious to see how long this can go on...

---

### Post by lavinog on 2010-04-09
> **HC48 said:**
> 9th April: computer still working, the warning message increases by a sector every other startup. Value = 71 for the moment. (Limit is supposed to be 63)
H :)

PS I have backed up of course but I'm curious to see how long this can go on...

Where did you get that the limit is 63?  Is that the threshold setting?
The value should be the actual sector count, the threshold should be comparing the normalized value.  The normalized value can start somewhere between 100 and 255 (each manufacturer does it different) and it counts down.  Once the normalized value is less than the threshold the SMART assessment fails.
There should be a couple thousand if not tens of thousands backup sectors available.  As mentioned before, just bumping your drive can increase this count sometimes.

It probably wouldn't hurt to keep track of this though.  If you are consistently getting a relocation every other boot knowing that your drive isn't being jarred around, then there might be something wrong.

---

### Post by Mark Phelps on 2010-04-09
I disagree about the usefulness of this utility being implemented by default.

New folks "coming over" from MS Windows are nervous enough about all the sudden changes they have to deal with.

Not knowing any better, they are going to take any error messages seriously -- and a utility telling them their hard disk is failing, true or not, is likely to induce the very kind of panic we want to avoid. 

And, that kind of panic is all to often the tone we see from these folks who are scared that all their stuff is suddenly going to vanish because their hard drive is failing.

Then, they have to rumage around trying to find and download more useful drive utilities.  And when they are successful in doing that, all too often, this other utility tells them their drive is fine!

Talk about giving new users a bad impression -- this is exactly what this utility is doing.

I agree with the others who said it should not have been included, knowing the buggy nature of its reporting.

---

### Post by lavinog on 2010-04-09
It seems less scary in lucid.
It was considered a feature when it was included.  The problem is that there is little documentation for SMART info so the warning was designed based on that it seemed like a serious issue.

---

### Post by HC48 on 2010-04-11
Hello, thank you for your message lavinog.
I got it  from the SMART data window, it's number 5 which is displayed in red, number of sectors reallocated, normal= 246, the worst= 246, threshold = 63, value = 74 sectors

It says "74 bad sectors "in the summary part and "many faulty sectors" in red, it advises backing up and changing the hard drive.
(I have made a screen shot with Gimp but haven't succeeded in posting it from Windows Live.:( If I type the URL am I supposed to see the image??? + my machine is all in French so I don't know if it's a good idea to use it.)

[IMG]http://cid-710e3418baf29610.skydrive.live.com/self.aspx/computer/Palimpsest.jpg[/IMG][IMG]http://cid-710e3418baf29610.skydrive.live.com/self.aspx/computer/Palimpsest.jpg[/IMG]Sorry I'm not very technical :icon_frown:... but happy to learn

Have a good day!

---

### Post by HC48 on 2010-04-11
got picture... yay![IMG]http://cid-710e3418baf29610.skydrive.live.com/self.aspx/computer/Palimpsest.jpg[/IMG]

---

### Post by HC48 on 2010-04-14
hello,
SMART is no longer available since yesterday! I didn't cancel it, it just decided to up and leave. :(

How do I get it back?

Thanks...

Other thread about this = [http://ubuntuforums.org/showthread.php?t=1454545&highlight=SMART+Palimpsest](http://ubuntuforums.org/showthread.php?t=1454545&highlight=SMART+Palimpsest)

Later: downloaded GSmartControl but it won't open, I get this message (I'm working in French):
"L'exécution du processus fils « su-to-root » a échoué (Aucun fichier ou dossier de ce type)", loosely translated (I think) = thread "su-to-root" failed (No file of this type)
I haven't the knowledge for this type of problem (yet...)
Any help?
Thank you
H :)

Later... tried using doc from ubuntu and terminal commands (very cautious here), computer says I have smartmontools ([http://doc.ubuntu-fr.org/smartmontools?s](http://doc.ubuntu-fr.org/smartmontools?s)[]=smart ) packets but still unable to get SMART working. Apparently the file doesn't exist. Need more time if I do this alone. I'll try another download perhaps. Would be good to get palimpsest working again tho too.

---

### Post by HC48 on 2010-04-15
Now I have found this: [http://ubuntuforums.org/showthread.php?t=1439140](http://ubuntuforums.org/showthread.php?t=1439140)

> **chrisccoulson said:**
> As I've just commented on the bug report that was opened, I'll post the same response here for people who didn't see that:
See [https://launchpad.net/bugs/553282](https://launchpad.net/bugs/553282)

I'm asking myself now if I have a the bug or if it's a symptom of HD failure...

---

### Post by lavinog on 2010-04-15
> **HC48 said:**
> Now I have found this: [http://ubuntuforums.org/showthread.php?t=1439140](http://ubuntuforums.org/showthread.php?t=1439140)

I'm asking myself now if I have a the bug or if it's a symptom of HD failure...

The bug is a feature.  SMART detection was disabled intentionally to prevent destroying some SSDs.

---

### Post by HC48 on 2010-04-15
Thanks again lavinog. I think I've understood now. I did try redownloading Palimpsest and Gsmartcontrol before seeing your message but no luck. I still don't have SMART.
I'll continue to study but don't really need it for now. I have backups if I crash.
H :)

---

### Post by HC48 on 2010-04-15
oops! How do we cancel a message?:lolflag:

---

### Post by lavinog on 2010-04-15
> **HC48 said:**
> oops! How do we cancel a message?:lolflag:

You can just edit your message and say something like "deleted."

---

### Post by HC48 on 2010-04-16
Thanks again
H :)

---

### Post by blazerqb11 on 2010-04-23
Arg, I just installed Ubuntu again after buying a new HDD.  After installation, the new HDD looked fine, but the older drive, the one that I installed it on, showed up as having over a thousand bad sectors, and it told me "drive failure" was imminent.  Just to be sure I checked a S.M.A.R.T. utility in Windows and it failed short and long test almost immediately several times, so I assumed the drive was going bad and filed and RMA with Western Digital.  For various reasons I then reformatted to NTFS in Windows and now S.M.A.R.T. passes a quick test and doesn't seem to be having any problems with a long test.  After the long test is finished I plan on running a full surface scan, but it is not looking like anything is gonna come up.  Ha, I wonder if I can get a refund from UPS for the shipping I already paid for.

Is it a problem with ext4 and S.M.A.R.T.?

---

### Post by john newbuntu on 2010-04-23
Do you want to check the drive once with WD's data lifeguard diagnostic tool?
[http://support.wdc.com/product/download.asp?lang=en](http://support.wdc.com/product/download.asp?lang=en)

---

### Post by P4man on 2010-04-23
SMART operates at a much lower level than a filesystem, it has nothing to do with Ext4, ntfs or any other filesystem. You can fill your drive with random 1 and 0's so it doesnt even have a filesystem and smart will still work.

Formatting your drive, if you did a normal and not a quick format, would access every sector of the drive and would trigger the drive's internal logic to relocate the problematic sectors to spare one's. In palimpsest this should show up in the relocated sector count.

This doesnt mean that your drive is a-ok now. Its probably still dying its slow death, though you can use it for now.

---

### Post by blazerqb11 on 2010-04-23
I ran a full surface scan with the WD diagnostics and it found bad sectors, so it seems the Linux diagnostic was correct.  I guess I'll be sending in that RMA after all.

> Formatting your drive, if you did a normal and not a quick format, would access every sector of the drive and would trigger the drive's internal logic to relocate the problematic sectors to spare one's

Hmm, I did a quick format to NTFS, so I wonder why SMART was failing (very quickly I might add) before formatting and was initially passing after.  However, I just ran another SMART test and it is failing once again.  I guess it must have remapped sectors, and now more have failed?

Edit: I just remembered that I wiped the drive in preparation of sending it in, so that is what must have triggered the remapping.  Therefore, now that more sectors have failed, I believe I can say with confidence that the drive is failing.

---

### Post by warfacegod on 2010-04-23
I got page six of this thread before getting sick of reading it. So I'm not sure if anyone has mentioned this yet.

Try using gsmartcontrol:

```
http://ubuntuforums.org/showthread.php?t=1259923
```

Run it's heaviest test. If you still get bad sector warnings, its a safe bet that your drive is failing. If not then ignore Palimpset. It has been throwing false positives since it was introduced in 9.04, and it doesn't look like its going to get fixed anytime soon.

The simplest way to disable the warning is go to:

System> Preferences> Startup Applications> and uncheck "Disk Notifications"

---

### Post by lotharmat on 2010-04-23
> **warfacegod said:**
> I got page six of this thread before getting sick of reading it. So I'm not sure if anyone has mentioned this yet.

Try using gsmartcontrol:

```
http://ubuntuforums.org/showthread.php?t=1259923
```


Dude - That's a link to an article on Bittorrent... :confused:

---

### Post by warfacegod on 2010-04-23
> **lotharmat said:**
> Dude - That's a link to an article on Bittorrent... :confused:

That's strange! I used Crtl+V to paste the code and when I saw that it was a link I posted for someone else, I typed the code out by hand. Regardless, my apologies. Here:

```
sudo apt-get install gsmartcontrol
```

---

### Post by HC48 on 2010-05-05
Hello again,
I have just installed Lucid and am happy to say it has got my old smartbase mp370 working again (the scanner) and gsmartcontrol says my HD is healthy.
I have a new HD waiting in the wings, just in case, but so far so good!
H :)

Later: Had second thoughts and checked HD with the programme in the system menu and the values are the same as with palimpsest. Consequently I have changed the HD and discarded the old one. Lucid up and running again in a healthy computer... :)

H :)

---

