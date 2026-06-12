---
title: "Is it possible to improve transfer rates?"
date: 2012-10-09
forum: General Help
---

### Post by temp03 on 2012-10-09
I'm extremely new to Ubuntu (downloaded just last week) and I'm trying to use it as a solution to a problem I have but things aren't going too well. I'm trying to rescue some data by using Ubuntu as my failing external freezes Windows Explorer. Luckily the drive mounts when using Ubuntu. 

What I am trying to do now is merge files and folders to reduce space and eliminate any duplicates I have but the process is EXTREMELY slow. I started at about 11kB/sec and now I seem to have topped off at 50.7kB/sec which isn't nearly fast enough. I have a lot of files to move. I can only imagine how long it is going to take when I have to move everything from my first dying external to my replacement external. 

Is there anything I can do to speed up this process? The transfer rate can't be this slow, right?

---

### Post by temp03 on 2012-10-09
If ANYONE could help at all it would be extremely helpful. As it is now, it will literally take weeks just to move ~100Gb. And I will need to transfer way more than that within a certain time frame. What can I do? The speed has already dropped back down to ~33kB/sec

I used disk utility and it does recognize the max speed is 480Mb/sec for USB 2.0

---

### Post by sienile on 2012-10-09
Since you say it's a failing drive, it's probably what is slowing down the process.

You MIGHT be able to speed things up by taking the disk out of its case and mounting it inside your computer. It's a slim chance, but it could help.

---

### Post by idoitprone on 2012-10-09
It not possible to improve rates with failing hardware, but it possible to reduce amount of things you are transfering

Use the rsync command.

If the files are alike with minor changes, then use it. 

Or else just use a simple copy because  the file differs enough that it is a waste of time.

It will use cpu cycles to compare both files to see what you will need to be to be copied.

---

### Post by temp03 on 2012-10-09
Ok. Thank you to both responses. In the meanwhile I also noticed that it is reported there are bad sectors to the drive. This is definitely the last time I buy a Western Digital. I'm pretty sure the replacement drive is a refurbished one instead of new as well. 

I'll see what I can do with rsync. Unfortunately, I am using a laptop so I cannot mount inside instead of using the external case. I just want to finish all the transfers within 4 weeks so I can send in the drive and get money back.

---

### Post by dcstar on 2012-10-10
> **temp03 said:**
> I'm extremely new to Ubuntu (downloaded just last week) and I'm trying to use it as a solution to a problem I have but things aren't going too well. I'm trying to rescue some data by using Ubuntu as my failing external freezes Windows Explorer. Luckily the drive mounts when using Ubuntu. 
..........

```
man ddrescue
```

---

### Post by GreatDanton on 2012-10-10
I just tried the previous command (man ddrescue) and I got this: No manual entry for ddrescue.

---

### Post by Mark Phelps on 2012-10-10
I sympathize with you about WD drives -- I had two of them, each only a few months old, fail on me within a two-week timeframe.

As to the drive speed, as long as there are bad sectors that are in use, the drive performance will be very s...l...o...w -- because it tries over and over again to read a sector until it finally gives up and moves on to the next one.

I tried to rescue data from my failing drives but the utilities all gave up early in my attempts with "too many failures".

---

### Post by temp03 on 2012-10-10
> **GreatDanton said:**
> I just tried the previous command (man ddrescue) and I got this: No manual entry for ddrescue.
  
@GreatDanton, Yeah, I had gotten(?, or is it got?) that message too but you can install it. Sorry I can't remember the actual command for it but I want to say: sudo apt-get install gddrescue

@dcstar, Thanks, I will try using this. I'm not very adept with Ubuntu and using the terminal yet but I'll keep doing research to try and do this so I can rescue my data

@Mark Phelps, Sorry to hear that. I think I need to count myself lucky that I got around 9 months out of mine before it suddenly quit on me for no reason. I'm lucky enough that it began spinning again and will only mount in Ubuntu. My warranty got me a new one sent in (while they hold onto my money until I send the defective one in) but a cursory search shows this drive is also not very highly rated on some sites. I'm going to try using disk utility as well to check and repair the filesystem but so far I'm not having too much luck. I'm going to get a Seagate after this.

---

