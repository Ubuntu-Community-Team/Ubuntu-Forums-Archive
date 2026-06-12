---
title: "Corruption Everywhere"
date: 2011-05-09
forum: General Help
---

### Post by Trevski13 on 2011-05-09
Hello, I'm (for the most part) running ubuntu 10.10 (also has 8.10, Windows XP, and Windows 7 [all of which have corruption problems too, although Ubuntu only recently started having problems]) on my HP Pavilion tx2000 and filesystem corruption is running rampant throughout my hard drive.  I have an SSD but data that's on other media also corrupts. Almost anytime I boot I have to run fsck to fix all the errors... and there are always a lot. It will also occasionally make the file system read only  At first it wasn't a big deal, nothing noticeable anyway. But then applications wouldn't run (not even terminal). Because of this the OS has become more or less useless. My first thought was the HD but that doesn't seem to be the case, second thought was RAM but I ran the built in RAM tester and it was clean... any ideas? I'd rather not have to reinstall my OS every month...

Any help would be appreciated.

---

### Post by Favux on 2011-05-09
Well you need an expert which isn't me.  But I'm pretty sure if smart disk is saying your hard drive is healthy then the culprit is likely to be bad RAM despite the OK check.  Especially since it is affecting another hard drive, the SSD.  You should probably try a more exhaustive memory check.

---

### Post by lmarmisa on 2011-05-09
I recommend to check the SMART status and data of your hard drive. Select System -> Administration -> Disk Utility.

---

### Post by Trevski13 on 2011-05-10
> **Favux said:**
> Well you need an expert which isn't me.  But I'm pretty sure if smart disk is saying your hard drive is healthy then the culprit is likely to be bad RAM despite the OK check.  Especially since it is affecting another hard drive, the SSD.  You should probably try a more exhaustive memory check.

thanks for the quick reply, what would be the best way of going about that? I know several methods for checking the RAM I'm just not sure what's considered "exhaustive"...

---

### Post by Favux on 2011-05-10
Hopefully a guru will drop by.

In the meantime do a quick scan of the memtest86 stuff and see what it says:
[http://www.memtest86.com/](http://www.memtest86.com/)
[http://www.custompcblog.com/troubleshooting/memtest86-memtest-86-tutorial-guide](http://www.custompcblog.com/troubleshooting/memtest86-memtest-86-tutorial-guide)
[http://www.overclockers.com/forums/showthread.php?t=409152](http://www.overclockers.com/forums/showthread.php?t=409152)

I'd imagine you'd want to pay particular attention to anything talking about testing read/write buffering and corruption.

---

### Post by mcduck on 2011-05-10
That *does* sound like broken RAM module, or of course anything motherboard- or PSU-related could also be the cause of such errors. It definitely is a hardware problem, that much can be said, since it affects multiple hard drives and operating systems.

Anyway, you said you ran the memtest, but did you just run it once through or did you leave it running for longer time? Memtest is supposed to be run multiple times through, as RAM errors often start appearing only after the memory has been under stress for long period of time. Running one memtest loop doesn't really tell you much.

I'd suggest letting memtest run at least overnight. If it passes *that*, then you might want to try swapping your motherboard or PSU if you know somebody who could borrow you one. Checking the voltage levels would be a good idea as well.

---

### Post by Trevski13 on 2011-05-22
> **mcduck said:**
> Anyway, you said you ran the memtest, but did you just run it once through or did you leave it running for longer time? Memtest is supposed to be run multiple times through, as RAM errors often start appearing only after the memory has been under stress for long period of time. Running one memtest loop doesn't really tell you much.

I'd suggest letting memtest run at least overnight. If it passes *that*, then you might want to try swapping your motherboard or PSU if you know somebody who could borrow you one. Checking the voltage levels would be a good idea as well.

I finally got around to running memtest for a long period of time. I ran it for about 24 hours (about 12 times through) and no errors showed up... unfortunately it's a laptop, so switching my motherboard/PSU is out of the question. Also I know where to easily test the voltage on a desktop but I'm not so sure about a laptop.

I was reading some of the stuff about memtest and one thing said that test 9 (bit fade) isn't run by default. Should I run that?

---

### Post by linuxinstalledfromhdd on 2011-05-22
It sounds like hardware to me.  I would keep swapping out older parts for new parts until it get resolved eventually.  I would start with the mb, ram, and power supply.  A new hard drive is a good idea too.

---

### Post by walt.smith1960 on 2011-05-22
Being a laptop makes it difficult.  A friend had a similar problem with her hard drive getting corrupted and having to do periodic reinstalls. The problem turned out to be an intermittent IDE data cable problem.

---

### Post by linuxinstalledfromhdd on 2011-05-22
How old is the laptop?  Did you get it used?  Make, model, etc?  Did you have any other problems with it before this new problem started?

---

### Post by cayphed on 2011-05-22
Perhaps try reading up on these, it may help,

[http://cquirke.mvps.org/9x/baddata.htm](http://cquirke.mvps.org/9x/baddata.htm)
[http://www.thexlab.com/faqs/repairprocess.html](http://www.thexlab.com/faqs/repairprocess.html)
[http://help.lockergnome.com/general/Corrupt-Hard-Drive-drive--ftopict52302.html](http://help.lockergnome.com/general/Corrupt-Hard-Drive-drive--ftopict52302.html)

How ever, what I have done for a friend in the past is remove the drive in question and plug it into
a different pc, least then I know if it's the drive or not.

---

### Post by Trevski13 on 2011-05-22
> **walt.smith1960 said:**
> Being a laptop makes it difficult.  A friend had a similar problem with her hard drive getting corrupted and having to do periodic reinstalls. The problem turned out to be an intermittent IDE data cable problem.

I can pretty much guarantee it's not a cable problem or a hard drive problem as the corruption has occurred on USB flash drives as well... (I installed an ran Ubuntu off a USB stick specifically for testing whether it would corrupt as well... and it did)

here are some facts clumped together:
[LIST]
[*]It's an HP pavilion laptop tx2000 (therefore PSU/Motherboard not (easily) replaceable) around 3-4 years old.
[*]Bought it new
[*]It is NOT under warranty 
[*]The hard drive not the original, it is an OCZ Agility 120GB SSD
[*]The hard drive's SMART data says it's healthy
[*]Other storage devices such as USB flash memory sticks also corrupt
[*]It has 3GB of original RAM (1x 1GB 1x 2GB I think)
[*]24 hours of memtest find no errors
[*]I thought the original HDD had gone bad (never actually checked) and replaced it with the current SSD (I still have the original)
[*]with both hard drives Windows (XP, Vista, 7) will just power off randomly (as if it was running on battery and you removed it)
[*]never had trouble with Ubuntu until recently
[*]I currently continue to use it running a live CD
[/LIST]

---

### Post by sharpbiohazard on 2011-05-22
I just got rid of my TX2000. That laptop (specifically the motherboard) is notorious for having overheating problems, specifically related to solder connections on the various chips. Mine had major problems with the built-in nVidia 6150 graphics card. I have experimented with overclocking on my PC (im a gamer) and it sounds like you are having RAM problems. Only errors that are so random could be attributed to that.

However, considering what I just said about the mobo, I am sure your RAM is fine. Instead, it is the internal connections on the motherboard that are making the RAM appear as the culprit.

A quick google search on this model of laptop will bring up hundreds of forum posts that all state the same problems. HP has refused to admit the error is on their end :(

---

### Post by Trevski13 on 2011-05-22
> **sharpbiohazard said:**
> I just got rid of my TX2000. That laptop (specifically the motherboard) is notorious for having overheating problems, specifically related to solder connections on the various chips. Mine had major problems with the built-in nVidia 6150 graphics card. I have experimented with overclocking on my PC (im a gamer) and it sounds like you are having RAM problems. Only errors that are so random could be attributed to that.

However, considering what I just said about the mobo, I am sure your RAM is fine. Instead, it is the internal connections on the motherboard that are making the RAM appear as the culprit.

A quick google search on this model of laptop will bring up hundreds of forum posts that all state the same problems. HP has refused to admit the error is on their end :(

Well sh*t...  When you say internal connections I assume you mean deeper than mobo to RAM connectors... Meaning reseating the Ram wouldn't help...

---

### Post by sharpbiohazard on 2011-05-22
> **Trevski13 said:**
> Well sh*t...  When you say internal connections I assume you mean deeper than mobo to RAM connectors... Meaning reseating the Ram wouldn't help...

Oh yeah. Like the small connections that exist IN the motherboard, the microscopic etchings. The only possible fix would be to get a new one, (which go in upwards of $100+ on ebay). At that point in my opinion it is just better to get a new laptop. The most random stuff has stemmed from this problem.

My wifi-card also crapped out because of this issue (or rather, it looked like it crapped out in Windows :P) The card was fine.

You could sell it for parts on ebay, I saw some going for $80+ if you have a good case with no cracks and everything else is in order. I do not know your situation in terms of if you need to keep the computer or not; just a suggestion.

---

### Post by Trevski13 on 2011-05-22
> **sharpbiohazard said:**
> Oh yeah. Like the small connections that exist IN the motherboard, the microscopic etchings. The only possible fix would be to get a new one, (which go in upwards of $100+ on ebay). At that point in my opinion it is just better to get a new laptop. The most random stuff has stemmed from this problem.

My wifi-card also crapped out because of this issue (or rather, it looked like it crapped out in Windows :P) The card was fine.

You could sell it for parts on ebay, I saw some going for $80+ if you have a good case with no cracks and everything else is in order. I do not know your situation in terms of if you need to keep the computer or not; just a suggestion.

I'm confident I have the ability to replace the parts, I'm just not sure I'm willing. And I'm not sure how I feel about selling it... I like small laptops and I *love* tablets... so I've been thinking about getting a Lenovo Thinkpad X220T but I don't have the money right now (it's not exactly cheap... but it's also not a piece of crap)

---

