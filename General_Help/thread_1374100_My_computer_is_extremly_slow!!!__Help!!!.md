---
title: "My computer is extremly slow!!!  Help!!!"
date: 2010-01-06
forum: General Help
---

### Post by subjugater on 2010-01-06
Hi, guys.

It seems that my desktop is in a big trouble. It takes one minute to start any application like firefox, open any file like a pdf document, and minimize a window. However, I can open a folder quickly without any delay. I can use Matlab normally after starting it (but it takes a while to start it.)

Is there anybody has such an experience? Should I clean my disk by using something like disk janitor? It appears that 8.0.4 doesn't have a janitor, while 9.0.4 does. 

BTW, I'm using ver8.0.4 and my desktop has a core-2-duo CPU. 

Pls. give some help. Thank you in advance.

---

### Post by oldos2er on 2010-01-06
What are your system specs, aside from CPU? Which desktop environment are you using?

---

### Post by subjugater on 2010-01-06
> **oldos2er said:**
> What are your system specs, aside from CPU? Which desktop environment are you using?

Dell Inspiron 530
Intel® Core™2 Duo Processor E6550 (4MB L2 Cache,2.33GHz,1333 FSB), 
Memory 	2GB Dual Channel DDR2 SDRAM at 667MHz- 2DIMMs
Video Cards 	Integrated Intel Graphics Media Accelerator 3100
Hard Drives 	250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™


I am not sure that I understand you correctly about the desktop environment. Do you mean the version of Ubuntu? It's 8.0.4.

Thanks a lot.

---

### Post by gradinaruvasile on 2010-01-06
Then its Gnome.
The comp should fly with that configuration. The only slow thing is the video card.
I have a Optiplex 755 at work, exactly this configuration (CPU/RAM, the   HDD is slower). But i have a Nvidia card on it (Quadro NVS 285). I used it with dual monitors and now with only one and compiz enabled with wobbly windows/fire effects and it flies. I have 2-3 weeks of uptimes on it between reboots, run all kinds of stuff on it, its really fast and rock stable. I use Ubuntu 9.04, but i used 8.04/8.10 too on it and it was the same.

Try disabling desktop effects if you have them on. The Intel IGPs have buggy and slow drivers sometimes (versions) that dont cope well with accelerated desktop effects.

Trust me, it doesnt have to do with fragmentation - i used on my work computer 8.10-9.04 without reinstall, just online upgrade and i have no problem regarding HDD speed.

---

### Post by subjugater on 2010-01-06
> **gradinaruvasile said:**
> Then its Gnome.
The comp should fly with that configuration. The only slow thing is the video card.
I have a Optiplex 755 at work, exactly this configuration (CPU/RAM, the   HDD is slower). But i have a Nvidia card on it (Quadro NVS 285). I used it with dual monitors and now with only one and compiz enabled with wobbly windows/fire effects and it flies. I have 2-3 weeks of uptimes on it between reboots, run all kinds of stuff on it, its really fast and rock stable. I use Ubuntu 9.04, but i used 8.04/8.10 too on it and it was the same.

Try disabling desktop effects if you have them on. The Intel IGPs have buggy and slow drivers sometimes (versions) that dont cope well with accelerated desktop effects.

Trust me, it doesnt have to do with fragmentation - i used on my work computer 8.10-9.04 without reinstall, just online upgrade and i have no problem regarding HDD speed.

Buddy, thanks for you comments. However, I don't have any desktop effects on. My computer turned out to be slow so suddenly. It was absolutely normal yesterday, but extremly retarded today. The only thing that I recall is that I was trying to open a very big text file (500MB) by gedit. It took forever to open, so I kill it by system monitor. After doing this, I shut down the computer and went home. Could this be a potential reason to explain why the computer is slow now?

Could you pls tell what I should do now? What should I do to check the computer and locate the problem?

---

### Post by subjugater on 2010-01-06
bump up

---

### Post by trpnblies7 on 2010-01-06
Have you checked System Monitor to see if any process is using a ton of memory?

---

### Post by Onesimus on 2010-01-06
It may be a failing hard disk.  You could try running SMART software to see if it detects anything suspect.

---

### Post by subjugater on 2010-01-06
> **Onesimus said:**
> It may be a failing hard disk.  You could try running SMART software to see if it detects anything suspect.

I have installed the SMART-notifier. But how should I use it? I didn't see any icon of it in the application list. 

BTW, why do you suspect that the problem is due to the hard disk? I can watch movie and download stuff normally. It's only pain in the neck when I am trying to open a movie or switch between windows.

Thank you so much anyhow.

---

### Post by subjugater on 2010-01-06
> **trpnblies7 said:**
> Have you checked System Monitor to see if any process is using a ton of memory?

Nothing abnormal :(

Thanks, man.

---

### Post by SecretCode on 2010-01-06
> **subjugater said:**
> I have installed the SMART-notifier. But how should I use it? I didn't see any icon of it in the application list. 
.

System > admin > disk utility; select your main hard disk if more than one is listed; and click the More information link in the right hand panel - if SMART is supported.

---

### Post by Onesimus on 2010-01-06
> **subjugater said:**
> I have installed the SMART-notifier. But how should I use it? I didn't see any icon of it in the application list. 

BTW, why do you suspect that the problem is due to the hard disk? I can watch movie and download stuff normally. It's only pain in the neck when I am trying to open a movie or switch between windows.

Thank you so much anyhow.

I wondered whether it might be a problem with the hard disk because if programs are taking ages to start, it may be that the OS is taking ages to read the executables, or taking ages to find them.

If you are watching movies from the hard disk, and there are no performance issues, then its unlikely to be the hard disk.  If you're watching movies from a DVD, then it may still be the hard disk.

The program you want to install is gsmartcontrol from Synaptic.

Your performance issues may have nothing to do with the hard disk, but it is least good to rule it out.

---

### Post by Onesimus on 2010-01-06
> **SecretCode said:**
> System > admin > disk utility; select your main hard disk if more than one is listed; and click the More information link in the right hand panel - if SMART is supported.

The OP is running Ubuntu 8.04, not 9.10.  I don't think disk utility came in until 9.10 (perhaps 9.04).

---

### Post by SecretCode on 2010-01-06
Oh, good point. Sorry

---

### Post by subjugater on 2010-01-06
> **Onesimus said:**
> I wondered whether it might be a problem with the hard disk because if programs are taking ages to start, it may be that the OS is taking ages to read the executables, or taking ages to find them.

If you are watching movies from the hard disk, and there are no performance issues, then its unlikely to be the hard disk.  If you're watching movies from a DVD, then it may still be the hard disk.

The program you want to install is gsmartcontrol from Synaptic.

Your performance issues may have nothing to do with the hard disk, but it is least good to rule it out.

Buddy, thanks for your comments. I agree with what you said. It may not be the problem of the hard disk, otherwise I won't play any movie smoothly.

The thing is that I even have a hard time to switch between tabs in a firefox window. 

BTW, I can't find gsmartcontrol from Synaptic, perhaps since I am using 8.0.4. I am wonder if there is some universal checker can help one to check everything (It is likely to be impossible). 

Anyhow, thank you.

---

### Post by todak on 2010-01-06
Use this ```
sudo smartctl -a /dev/sda
``` to see all smart data about your drive (the assumption being /dev/sd**a** is the drive you want to check). Then paste the results here.

---

### Post by subjugater on 2010-01-06
> **todak said:**
> Use this ```
sudo smartctl -a /dev/sda
``` to see all smart data about your drive (the assumption being /dev/sd**a** is the drive you want to check). Then paste the results here.

Thanks, buddy. I've done what you told. The results below is really beyond my universe. 

```

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3250310AS
Serial Number:    9RY0ZLZK
Firmware Version: 3.ADA
User Capacity:    250,000,000,000 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jan  6 19:06:16 2010 EST
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
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 (  64) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   097   097   070    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       566
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       52480748
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4640
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       566
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   070   061   045    Old_age   Always       -       522059806
194 Temperature_Celsius     0x0022   030   040   000    Old_age   Always       -       30 (Lifetime Min/Max 0/19)
195 Hardware_ECC_Recovered  0x001a   068   062   000    Old_age   Always       -       81488158
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -

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

### Post by todak on 2010-01-06
It appears that your drives heads are having a hard time hunting for and reading data off of the  drive platters as evidenced by the seek error and read error lines. Have you bumped or dropped the drive recently? It appears you may have crashed the heads and the drive is trying multiple times to read the data from the bad sections. That would explain why certain data is read quickly while the data trying to be read from the bad sections is taking forever.

---

### Post by subjugater on 2010-01-06
> **todak said:**
> It appears that your drives heads are having a hard time hunting for and reading data off of the  drive platters as evidenced by the seek error and read error lines. Have you bumped or dropped the drive recently? It appears you may have crashed the heads and the drive is trying multiple times to read the data from the bad sections. That would explain why certain data is read quickly while the data trying to be read from the bad sections is taking forever.

Thanks for your analysis. In fact, I didn't bump or drop the driver. It's a desktop. The problem came so suddenly and oddly. The computer worked well yesterday, but appears slow this morning.

I downloaded and uploaded frequently in the last month. Can this be the reason for crashing the heads and the drive? 

BTW, it takes ages to switch between the tabs in firefox. Should we attribute this to the hard disk?

Thanks a lot.

---

### Post by todak on 2010-01-06
Nevermind. I misread the table.

---

### Post by todak on 2010-01-06
Something is definitely wrong. Your seek error rate shows 52 million! I doubt that number is correct, but your drive may be failing. A realistic number would be somewhere between 0-100. I have and old 80GB WD drive that is my main work drive that has 30,000 hours of power-on time and it shows no errors of any kind. Your drive also shows a temp of 522 million degrees C! Somewher in the neighborhood of 30-40 C is normal. That might explain a lot! :D Something may truly be wrong with the drive, though. It might be wise to back up your data and get another drive.

---

### Post by happyhamster on 2010-01-06
Do you perhaps have a root partition that is nearly full? You can check with the command:

df

---

### Post by subjugater on 2010-01-06
> **happyhamster said:**
> Do you perhaps have a root partition that is nearly full? You can check with the command:

df

Hi, buddy. Thank you for your suggestion. I tried. None of the partition is full. The highest rate of occupation is only 71%, obviously not a dangerous figure.

---

### Post by subjugater on 2010-01-06
> **todak said:**
> Something is definitely wrong. Your seek error rate shows 52 million! I doubt that number is correct, but your drive may be failing. A realistic number would be somewhere between 0-100. I have and old 80GB WD drive that is my main work drive that has 30,000 hours of power-on time and it shows no errors of any kind. Your drive also shows a temp of 522 million degrees C! Somewher in the neighborhood of 30-40 C is normal. That might explain a lot! :D Something may truly be wrong with the drive, though. It might be wise to back up your data and get another drive.

Thanks, man. So you still think the problem is from the hard disk.

The most weird thing is that the computer can read and write normally. When I was backing up my stuff just now, I copied 90GB stuff from the computer to a portable hard drive without any problem. Does this imply something? Again, thanks.

---

### Post by blueridgedog on 2010-01-06
Just out of curiosity, do you have similar issues if you boot off the LiveCD that you used to install Ubuntu?

---

### Post by subjugater on 2010-01-06
> **blueridgedog said:**
> Just out of curiosity, do you have similar issues if you boot off the LiveCD that you used to install Ubuntu?

Do you mean that I may want to boot from the liveCD to see what happen? Thanks.

---

### Post by todak on 2010-01-07
From the data you pasted, it appears from the model number that you have a Seagate drive. They are known for producing ridiculously high numbers in diagnostic programs. Your drive may be OK after all. Open a terminal and type ```
top
``` then press the enter key, wait a few seconds and then press the **q** key. Then paste the results back here.

---

### Post by Onesimus on 2010-01-07
Having seen the output from smartctl, I reckon it probably isn't the harddisk.  I seen far bigger numbers than that, with drives working fine.

---

### Post by DJonsson2008 on 2010-01-07
* Whatever the case back up your data ASAP!
  to USB stick/DVD or another drive

In debugging such issues I've found the following 
effective if not essential.

* Boot with the LIVE CD ... do some browsing on the net
  and otherwise work with the machine for a few minutes
  to help verify the hardware is stable.
 
* Get a cheap 2nd hand HD and do a quick generic
  install of 8.04 for comparision purposes.

With my integrated Intel graphics I found getting an Nvidia card
a great help, although with 8.04 I still use generic VESA drivers.

---

### Post by Usabent on 2010-01-07
People please help me it says hard disk is failing. Is it true? GO to my thread sorry if im advertising! Hard diski gfaling false alarm?

---

