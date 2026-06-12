---
title: "Karmic is broken - AGAIN!"
date: 2010-02-28
forum: General Help
---

### Post by Gnusboy on 2010-02-28
This is a long post and I apologize, but I think background might be important. If anyone reads it, I could use some help. Thanks in advance.

I am about to wipe clean my hard drive for the 4th time since I started using Linux. It seems that every time I add anything but the simplest features available to Ubuntu, my system gets chewed up and I have to TRY a re-install. 

After searching through hours of posts here, posting my problem here, and then reading many, many tutorials and doing what is recommended, my system STILL will not boot. I could always fix a problem in Windows and I do not understand why it is so difficult to do the same with Ubuntu.

The hardware seems fine after it passed a couple drive integrity checks and it passed an overnight memtest. The entire system is about 6 months old.

AMD Phenom 4X Black
ASUS motherboard M3A76-EM
WD 640 GB hard drive 
4 GB GSkill ram (800 mhz)
Sony Optiarc DVD/CD burner

I ran a drive integrity check and it passed and it passed an over night memtest.
The entire system is about 6 months old.
After the 2nd fatal crash, I reformatted, made 2 partitions and was able to get Karmic up and running,
But when it booted, it first showed 2 kernals and 2 swap files, but it worked so I left it that way.

About a month ago another kernal appeared. but I thought it was and automatic upgrade, so I didn't worry. It worked and did not have the time to figure out how to erase the older kernals.

There are 3 versions of Karmic listed 9.10.14 , 9.10.17 , and 9.10.19 
There are also 3 swap files listed.
EXT 4


The header lists 9.10.19 as beta. Does this have relevance? It seemed to boot on all of them andas 9.10.19 was at the top and worked I used that. 
About 2-3 weeks ago odd things began happening.

With several windows open, Firefox 3.5 would suddenly crash for no apparent reason. It was fine when restarted, but then it started happening frequently, then it closed and would not restart and locked up the entire system. I hard booted, but it wouldn't get past the initial Ubuntu screen. Before the desktop opened, the screen would go black except for a spinning small white circle with dots (the waiting to load symbol?), then it would freeze everything and had to be hardbooted - this happened more than a dozen times before I decided on a complete re-install. That brings us to the present.

I tried using the recovery option in a 3 kernals several times. It seems to go through the removing and upgrading process, but then goes to a black screen It also freeze the system and I have to do a hard boot to release it.
 I have tried using the Live CD to repair it but no luck. Tried a complete install over the original and the same thing happens.

I think the only option now is to completely wipe the drive qand start over from new. I don't care about the data loss. I just want it to work.

Are there other options?

---

### Post by lavinog on 2010-02-28
Is this a 64bit or 32bit install?
What video card do you have?  Are you using any proprietary drivers?

Do you have flash installed? if so how did you install it?
Try removing flash and see if the problem persists.

Also try removing ureadahead since it has been known to cause instability.

---

### Post by theozzlives on 2010-02-28
Sounds like you have more than one install. you should only have 3 partitions:

1. / This is your main partition and only needs to be 10-20 GB
2. /home This contains all your documents and settings should take up the rest of the drive after boot and swap.
3. swap This should be at least the size of your RAM

---

### Post by Gnusboy on 2010-02-28
Lavinog:
The system will not boot from Hard Drive or Live CD and will not accept a clean install.
It's 64-bit AMD
The video card is integrated with the ASUS M3A78-EM motherboard with ATI Radeon HD3200 GPU
Flash 10 is installed via package manager (no problems)

---------------------------
Theozzlives:

"Sounds like you have more than one install. you should only have 3 partitions:

1. / This is your main partition and only needs to be 10-20 GB
2. /home This contains all your documents and settings should take up the rest of the drive after boot and swap.
3. swap This should be at least the size of your RAM"

Yes, I have re-installed Karmic 3X previously. I realize there should only be 1 partition, with the necessary sections. The 640 GB drive was partitioned into 2 smaller partitions. One side has has the original install of Jaunty, and a failed upgrade to Karmic.
The other partition has a clean install of Karmic - that was the one I was running until the crash. 
This partition was showing several /sba/ from 02 - 10
I have tried to use a variety of recovery processes in an attempt to save whatever data is available - including the LiveCD. However, the documentation is either non-existent, vague or not understandable by me.
I just found and loaded SystemRescueCD (It's been 2 full-days to get here and to learn the command lines.) I really do not know what in the hell I am doing or how to do it.

---

### Post by lavinog on 2010-02-28
> **Gnusboy said:**
> 
With several windows open, Firefox 3.5 would suddenly crash for no apparent reason. It was fine when restarted, but then it started happening frequently, then it closed and would not restart and locked up the entire system. I hard booted, but it wouldn't get past the initial Ubuntu screen. Before the desktop opened, the screen would go black except for a spinning small white circle with dots (the waiting to load symbol?), then it would freeze everything and had to be hardbooted - this happened more than a dozen times before I decided on a complete re-install. That brings us to the present.

These symptoms have been known to be caused by using 32bit flash in a 64bit install, and using certain versions of the proprietary ATI driver.

---

