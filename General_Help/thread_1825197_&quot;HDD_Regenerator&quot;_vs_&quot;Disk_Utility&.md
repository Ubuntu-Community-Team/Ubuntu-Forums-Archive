---
title: "&quot;HDD Regenerator&quot; vs &quot;Disk Utility&quot;"
date: 2011-08-14
forum: General Help
---

### Post by hyfanious on 2011-08-14
Hi
Dist Utility says that my HDD has 65545 bad sectors
I checked my HDD by "HDD Regenerator" and it reported no bad sector!
which one is correct??

---

### Post by mcduck on 2011-08-15
Never even heard of HDD Regenerator so I can't say much about how reliable it might be. (Although their explanations about repairing damaged hard rives using magnetic reversal sounds, to be honest, completely fake. :D)

But the best way to be absolutely sure is to download a SMART diagnostic tool from your hard drive's manufacturer's web site Pretty much every manufacturer has one available for free. And of course there's always smartmontools,which should be available in Ubuntu's repositories.

---

### Post by IT Support on 2011-08-15
> **mcduck said:**
> Never even heard of HDD Regenerator so I can't say much about how reliable it might be. (Although their explanations about repairing damaged hard rives using magnetic reversal sounds, to be honest, completely fake. :D)

But the best way to be absolutely sure is to download a SMART diagnostic tool from your hard drive's manufacturer's web site Pretty much every manufacturer has one available for free. And of course there's always smartmontools,which should be available in Ubuntu's repositories.

are you sure in this? :) i have tried regenerator  in my practise and it has help me  not  once  :) so  i think HDD regenerator is good piece of software  :)

It can repair software damages but not physical :)

---

### Post by mcduck on 2011-08-15
> **IT Support said:**
> are you sure in this? :) i have tried regenerator  in my practise and it has help me  not  once  :) so  i think HDD regenerator is good piece of software  :)

It can repair software damages but not physical :)

Well, that's the thing. Every operating system already includes tools for repairing informational damage on the disc, and tools for mapping out physically damaged areas (bad sectors). So you don't need to pay for a program to do that. That's what tools like fsck and chkdisc do.

However they are actually claiming to be able to fix bad sectors, which are *always* actual physical defects of the disc surface. And they claim to be able to do that without loosing data (which is quite funny, since any data on such damaged partition of disc surface is already lost).

(besides,  find it quite hard to trust a software that needs to advertise itself as "no spys, no ads, no virus", or a software that I can't find any decent review of, only loads of sites that give word-to-word the same marketing text as review that is found on the developer's web site. Claiming that "professionals prefer" their software, it would be nice to see at least a single professional review of it somewhere, especially considering the way they claim it to work is rather special to say the least.)

Anyway, this is kind of off-topic for this thread so I suppose it's best to leave this subject. :)

---

### Post by dcstar on 2011-08-15
> **mcduck said:**
> Well, that's the thing. Every operating system already includes tools for repairing informational damage on the disc, and tools for mapping out physically damaged areas (bad sectors). So you don't need to pay for a program to do that. **That's what tools like fsck and chkdisc do.**
........

And exactly where does fsck have an option for checking bad blocks?

e2fsck does (the "-c" option), but I cannot see anything in the generic fsck program for doing anything but what it is supposed to - check **filesystem** errors and fix them.

---

### Post by mcduck on 2011-08-15
> **dcstar said:**
> And exactly where does fsck have an option for checking bad blocks?

e2fsck does (the "-c" option), but I cannot see anything in the generic fsck program for doing anything but what it is supposed to - check **filesystem** errors and fix them.

Those were examples of programs that check and repair errors. Not a complete list of every program in existence, or suggestions for programs that do every possible type of repairs. :D

(Actually, if you read the post, you'll see that in no place do I make the claim that fsck would detect/remap/repair bad sectors!)

Anyway, if you weren't aware, fsck simply checks the target file system and then calls for the filesystem-specific tool to do the actual job. So if you run fsck on an Ext2/3/4 partition, you actually end running e2fsck. You can even add any filesystem-specific options to fsck command, it will pass them on to the tool that actually does the checking.

You might also want to try using badblocks directly if you specifically wish to scan and map bad sectors. Although like you even yourself mentioned, e2fsck (and thus also fsck) will also invoke badblocks for you if you so request.

edit: It should also be mentioned that any recently modern hard drive also includes built-in tools for reallocating bad sectors so you shouldn't have to do anything at all yourself, the hard drive's controller will do that automatically. Besides, the appearance of bad sectors on a drive is in most cases a sign that the drive is reaching it's end-of-life so whatever you do you are, at best, just buying yourself a little bit more time before the drive fails. So a simple SMART status check to see if there are bad sectors on the drive is usually the only tool you need, if there are more than a few bad sectors the best solution in long run is to just get a new drive as long as the old one is still working and you can get all your files out from it.

Considering the subject of this thread, this all is of course more or less irrelevant. The OP asked about the difference between the status report from Disk Utility and a third-party program, and in my first post I suggested that the best way to check which one is giving the right value is to use the hard drive manufacturer's own tool. They usually come as bootable CD's and are as reliable tools for checking the drive's status as you could possibly get.

---

### Post by IT Support on 2011-08-15
> **dcstar said:**
> And exactly where does fsck have an option for checking bad blocks?

e2fsck does (the "-c" option), but I cannot see anything in the generic fsck program for doing anything but what it is supposed to - check **filesystem** errors and fix them.

how i know, it can`t repare bad blocks

---

### Post by mcduck on 2011-08-15
> **IT Support said:**
> how i know, it can`t repare bad blocks

Based on the fact that bad sectors are physical defects of the disc surface, *nothing* can repair them. They are usually simply marked and the data is mapped to another location on the disc.

Perhaps the HDD Regenerator actually *is* able to do that, but at least based on the lack of any decent information from the developer, and complete lack of proper tests of the software, it could just as well simply reallocate the bad sectors just like any other tool does. Or not do anything at all, really. What they tell on the web site is pretty much around the level of marketing magical healing crystal pyramids. "what actually happens is HDD Regenerator is strengthening Hdd magnetic surface by reading and writing repeatedly.", is the best they say on the site. :)

---

### Post by dcstar on 2011-08-15
> **mcduck said:**
> 
..........
Considering the subject of this thread, this all is of course more or less irrelevant. The OP asked about the difference between the status report from Disk Utility and a third-party program, and in my first post I suggested that the best way to check which one is giving the right value is to use the hard drive manufacturer's own tool. They usually come as bootable CD's and are as reliable tools for checking the drive's status as you could possibly get.

There was an issue originally with the Disk Utility (palimpsest) & **libatasmart4** library incorrectly reporting bad blocks even though there actually weren't any (the forums are full of posts reporting this). I imagine that this has been fixed in a later version but if the OP is still running that original version then it could explain his question.

I use 10.04 but I have never experienced the issue, it may well be a particular hard drive/hardware combo that causes it.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by IT Support on 2011-08-15
> **mcduck said:**
> Based on the fact that bad sectors are physical defects of the disc surface, *nothing* can repair them. They are usually simply marked and the data is mapped to another location on the disc.

Perhaps the HDD Regenerator actually *is* able to do that, but at least based on the lack of any decent information from the developer, and complete lack of proper tests of the software, it could just as well simply reallocate the bad sectors just like any other tool does. Or not do anything at all, really. What they tell on the web site is pretty much around the level of marketing magical healing crystal pyramids. "what actually happens is HDD Regenerator is strengthening Hdd magnetic surface by reading and writing repeatedly.", is the best they say on the site. :)

I had in my practice not one case thet HDD regenerator repair  HDD and i saw it with my eyes :D  so i still think that HDD regenerato is doing job well :)  and  i know that bad blocks isn`t only physical damage of HDD there  is  software damage too  :) so  i will repeat that HDDregenerator can correct software damage, not physical 




I am  finishing  posting about HDD regenerator , I wrote  not a little about it  :D
with the best regards :popcorn:
  

best regards

---

### Post by hyfanious on 2011-08-16
hey guys
thanks to ur advise
I installed Gsmartcontrol and U know it was recommended by my manufacturing HDD site ;) cool
I did that and run an extended test and my results is as the same as before
so I am a bit bewildered
there is a summary of my result:
```

  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       65545
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       4294901774
190 Airflow_Temperature_Cel 0x0022   054   037   045    Old_age   Always   In_the_past 46 (Lifetime Min/Max 33/53)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1

```now, does my hdd have any physical/non-physical bad-sector?

---

### Post by mcduck on 2011-08-16
> **hyfanious said:**
> hey guys
thanks to ur advise
I installed Gsmartcontrol and U know it was recommended by my manufacturing HDD site ;) cool
I did that and run an extended test and my results is as the same as before
so I am a bit bewildered
there is a summary of my result:
```

  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       65545
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       4294901774
190 Airflow_Temperature_Cel 0x0022   054   037   045    Old_age   Always   In_the_past 46 (Lifetime Min/Max 33/53)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1

```now, does my hdd have any physical/non-physical bad-sector?

Yes, it has 65545 bad sectors (which are always physical errors. a non-physical error of data on the disc would be a filesystem error, not a bad sector). And that's a serious amount of and sectors, so the "pre-fail" warning is definitely something to be worried about.

If I were you I'd back up all the important data from the drive now, and start looking for a new drive, preferably before the old one fails completely.

---

### Post by hyfanious on 2011-08-16
wow sounds awful
but whats ur opinion about this part of information :
[B]Overall health self-assessment test PASSED

[/B]and what does "pre-fail" mean exactly?
and what about "Old-age" one?
(I guessed it means that parameter had once failed before, and maybe no more threat ;) )

and in my estimation 65000 sector is something about 30mb, is that really as bad as u told?? (just 30 mb in 320 GB :) )

---

### Post by hyfanious on 2011-08-16
So if u are right and my HDD has really about 65000 bad sectors, so HDD Regenerator is definitely nothing but a piece of crap

---

### Post by hyfanious on 2011-08-16
sorry for being verbose
but since u mentioned the "pre-fail" is a serious problem can u see whole result and let me know ur opinion?
tnx in advance
here is my result:
```

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0025   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0023   142   100   033    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       3918
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       65545
  7 Seek_Error_Rate         0x002f   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -       7168
 10 Spin_Retry_Count        0x0033   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       3793
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       4294901774
188 Unknown_Attribute       0x0032   090   070   000    Old_age   Always       -       2686
190 Airflow_Temperature_Cel 0x0022   053   037   045    Old_age   Always   In_the_past 47 (Lifetime Min/Max 34/50)
191 G-Sense_Error_Rate      0x0032   098   098   000    Old_age   Always       -       753
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       26214800
193 Load_Cycle_Count        0x0032   086   086   000    Old_age   Always       -       141747
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x002a   100   099   000    Old_age   Always       -       0


```

---

### Post by mdshann on 2011-08-16
What brand is this hard drive? I use Seagate Seatools Diagnostics software if I am just looking to test the hard drive by itself. Seatools is available as a free download from [Seagate's Web Site]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD"). There is a Windows Version and a DOS version. The DOS version is an .iso files that you burn to a CD using an image burning software and then you boot from it and follow the prompts. This will tell you if you have bad blocks not just by looking at the SMART data but by actually doing a sector-by-sector scan. If it says there are bad sectors then you can be sure that the drive is bad. If it finds any bad sectors it is a good idea to at least back up your data and do it regularly if you do not plan on replacing the drive right away. In my experience SMART is always right when it says there is a problem, but not always right when it says the drive is OK!

To give you some idea, I repair about 100 computers a week. The most common issue is viruses of course, but the second most common issue I see is hard drive failure.

---

### Post by hyfanious on 2011-08-17
> **mdshann said:**
> What brand is this hard drive? I use Seagate Seatools Diagnostics software if I am just looking to test the hard drive by itself. Seatools is available as a free download from [Seagate's Web Site]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD"). There is a Windows Version and a DOS version. The DOS version is an .iso files that you burn to a CD using an image burning software and then you boot from it and follow the prompts. This will tell you if you have bad blocks not just by looking at the SMART data but by actually doing a sector-by-sector scan. If it says there are bad sectors then you can be sure that the drive is bad. If it finds any bad sectors it is a good idea to at least back up your data and do it regularly if you do not plan on replacing the drive right away. In my experience SMART is always right when it says there is a problem, but not always right when it says the drive is OK!

To give you some idea, I repair about 100 computers a week. The most common issue is viruses of course, but the second most common issue I see is hard drive failure.

tnx for ur reply
mine is HITACHI (Hitachi HTS725032A9A364) (320 GB) (7200 rpm)
I have another info to share
this HDD is not my original netbook HDD, as a matter of fact it was for my friend's notebook (a hp one) and we exchanged our HDDs, she was not so watchful about her electronics devices ;) (she is a bit active cute girl) and as I remember this amount of bad sectors are shown for a long time , almost 6 months, and I got this HDD about 10 months ago, so I guess these bad sectors maybe caused by my friend, and since these amount of bad sectors remain constantly as quantity, is it possible this HDD works for me for a long time from now?
if not , in ur estimation what is my confidence interval for expecting probably work of this HDD
_**(I had NEVER lost any DATA in this case**_)
tnx in advance

---

### Post by hyfanious on 2011-08-17
ok guys I am totally puzzled!!!!!
I tested my hdd by its manufacturing diagnostic program (downloaded from its site) and it takes about 1 hour to do a thorough test and finally report:

_**NO PROBLEM**_


!!!!!!!!!

I guess I owe an apologize to HDD Regenerator!!

Now whats ur advice
**I am totally bewildered, which these results are correct finally???**

---

### Post by hyfanious on 2011-08-17
> **mdshann said:**
> What brand is this hard drive? I use Seagate Seatools Diagnostics software if I am just looking to test the hard drive by itself. Seatools is available as a free download from [Seagate's Web Site]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD"). There is a Windows Version and a DOS version. The DOS version is an .iso files that you burn to a CD using an image burning software and then you boot from it and follow the prompts. This will tell you if you have bad blocks not just by looking at the SMART data but by actually doing a sector-by-sector scan. If it says there are bad sectors then you can be sure that the drive is bad.

I run an advanced test by Seagate Live CD and it reported "PASSED" as the result
I guess by running Seagate and Hitachi diagnostic programs and reporting no problem, my hdd should have no bad-sector and so : the dist utility must have a big bug!

---

### Post by hyfanious on 2011-08-18
since it seems that SMART data are junks ones, how can I reset them?

---

### Post by mdshann on 2011-09-28
Sorry to take so long to respond. If the manufacturers test and Seatools say that the drive is ok then it probably is. Strangely enough I have seen the 65545 number before and I wonder if it is a bug or something in Disk Utility. If the drive is at all in question then maybe you should replace it either way, or at least keep an up to date backup of it just in case something happens. Drives are getting pretty cheap these days, a 320GB drive can be had for about $40-50 USD.

---

