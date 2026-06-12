---
title: "Hard Drive Failure is Imminent"
date: 2010-09-30
forum: General Help
---

### Post by moederre on 2010-09-30
I am trying Ubuntu off a CD onto a Windows XP installed over a non working Windows 98. Ubuntu is warning me that the Hard Disk is going to fail, what should I do??

---

### Post by Grenage on 2010-09-30
Is it possible that the non-working Win98 installation is non-working because the hard drive is failing?

I've seen Ubuntu have false-positives on drive alerts (I assume it's SMART based).  Keep using the system, see if it crashes.

---

### Post by julio_cortez on 2010-09-30
And before it crashes unexpectedly.. Be sure you make a backup of every important data you have on the disk.. **Better safe than sorry!! **:)

---

### Post by psusi on 2010-09-30
What EXACTLY does the disk utility say about the drive?  Some drives report bogus information that leads to that warning, but it is likely that your drive is failing and you want to ditch it.

---

### Post by moederre on 2010-09-30
psusi.....How do I get to the Disk Utility from Ubuntu? Seems Ubuntu is the only thing that will run on this Hard Drive now. It did crash awhile ago when I tried to send this reply before. Now XP won't come up so I am back on the Ubuntu CD. 
What should the Disk Utility tell me and then what do I do?

---

### Post by psusi on 2010-09-30
Launch the disk utility from the menu.  Click on the drive, and hit the SMART button.  It should have a bunch of statistics listed and a button to initiate an extended self test.

---

### Post by jocko on 2010-09-30
> **moederre said:**
> psusi.....How do I get to the Disk Utility from Ubuntu? Seems Ubuntu is the only thing that will run on this Hard Drive now. It did crash awhile ago when I tried to send this reply before. Now XP won't come up so I am back on the Ubuntu CD. 
What should the Disk Utility tell me and then what do I do?
If your computer has been running since the windows 98 days, chances are that the disk is simply reaching the end of it's life. I've had several hard drive failures in drives that were "just" 3-6 years old... One failed without any warning whatsoever and others just start to degrade over time, loose parts of files and damaging the file system (and making the operating system anything from slightly unstable to completely useless) now and then...
If the drive is old, get a new one (but if the rest of the computer is old, maybe it's time for a new computer instead?).

---

### Post by moederre on 2010-09-30
Thanks jocko. Yes, the computer is old but I am trying to fix it up for a friend who just wants it for a backup and doesn't want to spend more that about $100. So, guess I'll look online  for a replacement HD, it'll have to be compatible. Also she'll need more memory, it's only got 512 now. 
So, anyone with ideas of where to get a hard drive that would be compatible with an older computer?

---

### Post by cogier on 2010-09-30
Have a look at **System>Administration>Disk Utility**. There is a lot of info there. Look for the time the drive has been running. I have a drive that is showing signs of failing but it's been running for over 4 years?

---

### Post by moederre on 2010-09-30
Thanks psusi, I will try that.

---

### Post by moederre on 2010-09-30
Thanks psusi and cogier, I did the SMART button and the errors are in #5 and #197 and all have to do with failures in "Remapping sectors and reallocating" 
And it shows only 3.5 years on the time of the HD
Do you all think if I just go ahead and install this ubuntu rather than running it off the CD it might fix all that??

---

### Post by psusi on 2010-09-30
Pending can be fixed by forcing the drive to write to the sector, which will either work, or remap it.  Already remapped means you had some unrepairable sectors and they have been replaced from the spare pool.  How many of each are there?  Run the extended self test to scan the whole drive.

If there are only a few, then you can probably live with it.  If it is more than a few, then back up anything you can still get that matters and toss the drive.

---

### Post by dFlyer on 2010-09-30
Backup any data you need to save and replace the hard drive ASAP. With the price of HDD being so cheap, it doesn't pay to take a chance the drive will fails.

---

### Post by garner_nc on 2010-09-30
If your friend just needs a backup machine you can run something like DamnSmall Linux easily with the 512Mb memory you have. A simple home file server / backup machine is neither memory nor CPU intensive. Buy a new drive, skip the memory.

All the Best,
D. White

---

### Post by moederre on 2010-09-30
psusi, and others, I did what I think is the total system test and the report didn't show anything wrong so I am just going to reformat this with Ubutu and see how it responds. Don't have anything on here that needs saved. Going to start over, with Ubutu installation. If it still shows HD failure inninent I will get a new HD. 
Thank you all for your help, I will let you know my results after the install.

---

### Post by psusi on 2010-09-30
What are the numbers for attributes #5 and #197?  If there are any in #197 you will want to force a write to the affected areas to try and fix them.  If #5 is more than a few, then you should keep an eye on it and run the extended self test periodically and if it increases, the drive is dieing.

---

### Post by moederre on 2010-09-30
psusi...I did the SMART button again and get different numbers now, that is, I don't see #5 and #197 now, they start with #211 with no red warnings. But I do remember that in #5 it was something like 196 or more and in #197 it was on 5 or so. Guess I have to look for a compatible HD. Trouble is finding one that works with an older computer.

---

### Post by psusi on 2010-09-30
Scroll the window.  There are more values than will fit on the screen at once.

---

### Post by moederre on 2010-09-30
Well psusi and others, it's all a mute point now, it did crash when I tried to fully install Ubuntu. The install had errors and couldn't even half finish. I can still run Ubuntu from the CD but when I look to see what is wrong with C drive, it doesn't even show there is one! So guess it's a lost cause. Thanks for all your help everyone! 
Anyone have ideas of how I can find out what Hard Drive to even look for to buy??

---

### Post by Grenage on 2010-10-01
Be thankful it happened now, and not in a month, when your friend has loads of data on it.

You'll likely be looking at an IDE drive, and there may well be a maximum hard drive size that the motherboard can support.  This can sometimes be increased with a BIOS update; check the model number on the internet.

---

### Post by psusi on 2010-10-01
> **Grenage said:**
> Be thankful it happened now, and not in a month, when your friend has loads of data on it.

You'll likely be looking at an IDE drive, and there may well be a maximum hard drive size that the motherboard can support.  This can sometimes be increased with a BIOS update; check the model number on the internet.

Generally you can use any size disk, but the bios may not be able to BOOT from beyond a certain point.  You can get around that by creating a small /boot partition at the start of the drive.

Oh, and FYI moederre, it is MOOT point, not mute.

---

### Post by Grenage on 2010-10-01
> **psusi said:**
> Generally you can use any size disk, but the bios may not be able to BOOT from beyond a certain point.  You can get around that by creating a small /boot partition at the start of the drive.

That's quite true.  I only mention it because I've seen a couple of machines have issues with the concept of a large drive.  A couple out of many hundreds, but it never hurts to play it safe if you're splashing cash.

---

### Post by moederre on 2010-10-01
Thank you Genage and psusi, It is definitely a dead hard drive. I will look for a new one that is IDE. Hopefully I can find one that is only about 20 GB so that the bios can handle it. Or make a partition if I have to. 
And thanks psusi for the correction in my spelling, had I sat back and thought a minute I would have realized I was spelling it wrong but had my head full of the quandary over the death of the hard drive. 
Thanks to everyone who gave advice. Been a nice experience to work with Ubuntu and the forums.

---

