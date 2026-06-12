---
title: "Single Ethernet Port Failure?"
date: 2010-05-07
forum: General Help
---

### Post by Penguin Guy on 2010-05-07
I keep on getting intermittent ethernet failures using a Gigabyte GA-MA790FXT-UD5P 790FX motherboard with a built-in network card. This is a problem on all operating systems.

After many intermittent failures I think I've finally found the solution; turn the PSU off, wait until the CMOS light goes off (about 15 seconds), then turn the PSU back on. It appears a bug with Linux where a setting on the firmware of the network card is occasionally incorrectly modified causing it to malfunction, when power is removed from the device the setting resets to default and normal functionality is restored.

---

### Post by dino99 on 2010-05-07
check ifconfig

---

### Post by Penguin Guy on 2010-05-07
> **dino99 said:**
> check ifconfig
Just added the output to the original post but it doesn't look like there's anything of interest in it.

---

### Post by Penguin Guy on 2010-06-16
Bump.

---

### Post by iponeverything on 2010-06-16
It may have gotten a funky firmware load. If you remove it from power for about 10 or 15 minutes, it may clear it. 

Though, it is not very unusual for ethernet hardware to fail. I have seen it quite a bit over the years..

---

### Post by yeleek on 2010-06-16
Realtek card?  Try this

[http://ubuntuforums.org/showthread.php?t=1509781](http://ubuntuforums.org/showthread.php?t=1509781)

---

### Post by Penguin Guy on 2010-06-16
> **yeleek said:**
> Realtek card?  Try this

[http://ubuntuforums.org/showthread.php?t=1509781](http://ubuntuforums.org/showthread.php?t=1509781)
As I said, it doesn't work in any operating system.

> **iponeverything said:**
> It may have gotten a funky firmware load. If you remove it from power for about 10 or 15 minutes, it may clear it. 

Though, it is not very unusual for ethernet hardware to fail. I have seen it quite a bit over the years..
I've had this problem for over a month now, so it's definitely been powered off for that amount of time. I've only had this computer for a year and wouldn't have expected a hardware failure, is it possible that it could be a loose wire or something?

---

### Post by iponeverything on 2010-06-16
> **Penguin Guy said:**
> As I said, it doesn't work in any operating system.


I've had this problem for over a month now, so it's definitely been powered off for that amount of time. I've only had this computer for a year and wouldn't have expected a hardware failure, is it possible that it could be a loose wire or something?

The connector is probably a surface mount, you could take a look at it to see if has bad soldier joint.

---

### Post by Penguin Guy on 2010-07-02
Both ports are now intermittently ceasing to function, however it's easily fixed by removing and reattaching the cable.

---

### Post by BatteryKing on 2010-07-02
The GA-EX58-UD5 is a defective motherboard.  I should know, I have one.  Also Gigabyte is refusing to honer their warranty on this board by sending the same defective motherboard back to me, claiming it has no defects.

Here is what I have had to do:  I bought an EVGA board and moved all of my components over to it.  The EVGA board is 100% stable, the Ethernet ports work on it, everything is fine.  The Gigabyte board with all of the same components on it doesn't even boot (can't detect boot drive any more and was always intermittent about it before) and Gigabyte still claims it is "defect free".  What a load of baloney!

I say boycott Gigabyte because their stuff don't work and they sham you out of your warranty.  Does anybody know of a class action lawsuit over these defective products?  Or should we start one now on this forum?  I mean this is $300 Gigabyte is scamming me out of and I don't appreciate it.

---

### Post by Penguin Guy on 2010-07-03
At the moment the problem isn't bad enough to warrant getting a new motherboard, but if it does reach that level then I'm going to demand recompense. The EVGA motherboards look quite good, if I do have further problems I'll definitely look into getting one of them.

---

### Post by Penguin Guy on 2010-07-06
I had a complete failure so I was forced to find a solution myself. After a bit of messing around I discovered that it's actually the cable that's the problem.

---

### Post by Penguin Guy on 2010-07-11
Wow, I just had it completely conk out twice for a few hours, if it continues I'll have to seriously consider replacing the motherboard.

---

