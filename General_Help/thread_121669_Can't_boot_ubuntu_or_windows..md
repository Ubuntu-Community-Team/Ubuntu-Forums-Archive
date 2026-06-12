---
title: "Can't boot ubuntu or windows."
date: 2006-01-25
forum: General Help
---

### Post by frost_ad on 2006-01-25
Looks like big trouble here. Recently ubuntu froze up on me a few times. Couldn't move mouse and no keystrokes did anything either. So I did a hard shutdown and rebooted. Everything seemed fine. The last time it froze and I was forced to shut it down I can't boot into either Windows or Ubuntu. The grub menu will come up but either os that I select will freeze up in the boot process. Ubuntu seems to freeze at ```
Uncompressing Linux... Ok, booting the Kernel
```
Windows will stall at the XP splash screen or if I try safe mode it will freeze when checking through dll or sys files. 

Any suggestions? Is this a hardware or software problem? Is there anything I can check by booting with a live cd? Thanks to any and all suggestions!!

---

### Post by tim15856 on 2006-01-25
Try booting with the live CD. If it's a hardware problem, it may show up. It could be a memory or hard drive problem.

---

### Post by frost_ad on 2006-01-25
Ok, I ran the mem test option from the grub menu. After doing that I was able to boot into ubuntu.

Does this give any forsight into a problem? 

Also I'm not sure if this is related at all but this problem did seem to surface after I started using Azureus recently.

Any insight into any precautions I should be taking now, or anything I should be checking while I'm able to get in ubuntu would be appreciated.

---

### Post by frost_ad on 2006-01-25
Ok, it froze on me again. A little different this time.
At some point while I was away it froze and all I had was a black screen. Couldn't do anything to revive it (mouse movements, keystrokes). 
Here is the really weird thing. Maybe it's just coincidence but last time it froze like this with the black screen my wireless connection on my laptop went out and wouldn't came back unless I rebooted. Same thing happened to my laptop just now when the desktop froze. I know that's out there but I thought I'd mention in case by some off chance that gives someone some insight.

I'm running the memtest again and will see if it fixes my problem again. Anyone have any ideas? Did my RAM go bad on me?

---

### Post by dcstar on 2006-01-25
[QUOTE=frost_ad]
.......
I'm running the memtest again and will see if it fixes my problem again. Anyone have any ideas? Did my RAM go bad on me?[/QUOTE]
What CPU temp does your BIOS report?

---

### Post by poiuytr on 2006-01-25
You might be right about the memory problems - I'm not sure if memtest corrects for RAM errors, but if so, then it seems telling that you were actually able to boot only after you memtested.

I had very similar problems with my child's computer, and it turned out to be bad RAM.  I removed the bad stick (through trial and error) and all problems cleared right up.  

After that experience, whenever I now buy RAM, I always try to buy multiple sticks (i.e.  4 sticks of 250M RAM instead of 1 stick of 1GB RAM).

---

### Post by frost_ad on 2006-01-25
This computer has the original RAM from the factory (emachines). The computer is about 2.5 years old. Is it common for RAM to just go bad?

---

### Post by harryc on 2006-01-25
It's fairly common for RAM to go bad, yes. Try looping memtest86 overnight.

---

### Post by bb002 on 2006-01-25
does the Emachine run on Intel P4 processor? This past month and a half I've had a 3 people bring me their desktop (all dells running on P4's) saying it started freezing alot, not booting up, and randomly powering off. After giving their machine a complete hardware look over (I always look at the hardware first, seems to fix 50% of the computers brought to me) I noticed that the heatsink was held down by 2 metal clips attached to a plastic bracket. The plastic bracket had broken where one of the clips met it. This caused the heatsink to sit lopsided on the processor, which in turned caused overheating and the symptoms experience by the user.

The machines I'm talking about had 478 socket design. With the dell's they had some special design on the inside that would have made getting a new heatsink w/ bracket difficult since it would have messed up case airflow. Dell had some green plastic thing that covered the head sink perfectly to suck air out of the case. So I opted to get a metal bracket to replace the broken plastic one. I found one at [www.coolerguys.com](www.coolerguys.com) ([direct link](http://www.coolerguys.com/840556062097.html)). The bracket itself is cheap (but tough i tried to bent it had limited results.), it is the shipping and handling that costed my arm.

---

### Post by frost_ad on 2006-01-25
dcstar: I haven't checked. I don't think it is an overheating problem though. But after the memtest I will check.

bb002: No it's not a P4. It has an AMD Athlon 2600

harryc: I'm running memtest right now. It's on pass 6 currently. What exactly does memtest do? Will it "fix" anything, or simply let me know if something is wrong?


Thanks for all the help and suggestions so far.

---

### Post by harryc on 2006-01-25
Memtest doesn't fix a thing :). It will just stress test your RAM, but sometimes it takes several hours of testing, particularly to find intermittent problems.

---

### Post by frost_ad on 2006-01-26
Ok, went through memtest for 6 hours with no errors. Booted up ubuntu seemed fine for a couple of hours. Now it just restarted the machine. This happened while I was unpacking a rar file. 

Edit** rebooted the machine tried to unpack that rar file again and it froze. Can't move mouse can't do anything with the keyboard.

---

### Post by three_sixteen on 2006-01-26
[QUOTE=frost_ad]Ok, went through memtest for 6 hours with no errors. Booted up ubuntu seemed fine for a couple of hours. Now it just restarted the machine. This happened while I was unpacking a rar file. 

Edit** rebooted the machine tried to unpack that rar file again and it froze. Can't move mouse can't do anything with the keyboard.[/QUOTE]

Just from this post I really think that something is overheating.  Maybe your CPU or PSU fans aren't working as well as they should be, or heat isn't transferring off of your CPU or GPU -> heatsink properly.

---

### Post by harryc on 2006-01-26
Maybe this is asking for alot from an emachines, but can you get into BIOS and take a look at your voltages and CPU temperatures? For voltages you don't want any deviation more than +- 5%. Temps can vary depending on your CPU, but I'd begin to be concerned at anything over 70*c or so on that AMD of yours. From my experience, spontaneous reboots are usually power related, freezes are usually heat, RAM, or video driver.

---

### Post by frost_ad on 2006-01-26
Ok, I will try that when I get back to it and post an update.


Thanks again to everyone for all the help!

EDIT** Voltages all look good. I'm pretty sure I found the problem though. CPU tem was 68 Celsisus. I think the problem is this

Chasis Fan Speed:  0 RPM

Am I correct in assuming that fan went out and I need to replace it?

---

### Post by frost_ad on 2006-01-28
Ok an update. First off, referring to my last post I am now thinking that my case fan might not even have a monitor on it. Secondly I got a kernel panic. Said something about "not syncing" and "tried to kill init" I think. I was finally able to boot back into ubuntu but only after running memtest for an hour or so. Thirdly, twice now my pc just booted up on it's own out of nowhere.

Any ideas? I haven't opened up the case yet. I haven't had the time to pull my desk out and get to all the usb cables etc. so that I can pull the case out to open it. Maybe once I get in there I'll be able to see what the problem is.

Thanks again to all those that have helped.

---

### Post by allenmaher on 2006-03-20
I have an Athlon (same chip as you) that has recently been exhibiting the same behaviour...  the problem was in the heat disipation,  the fan on the power supply over time became clogged with dust and worked less, likewise the CPU fan and heat sink was coated in dust.  Giving it a good cleaning made a world of difference.  It still locks up if I run it hard (Neverwinter Nights for a few hours for example) for extended periods of time, but now it just crashes once or twice per day.

I will be rplacing the old powersupply and getting a better CPU fan and heat sink...  that should make a world of difference.

---

