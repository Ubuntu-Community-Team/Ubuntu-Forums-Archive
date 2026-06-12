---
title: "Very slow boot time on AMD ~30m"
date: 2011-03-21
forum: General Help
---

### Post by desperatenoob on 2011-03-21
I know this has been discussed several times. I've been reading these forums for the past 14 months and I still haven't found the solution on these forums.
I've been a long time Windows user, but I've started a small firm and because of lack of funds, I've decided to install Ubuntu on my company's PCs.
I have 8 PCs in total - 6 of them with Intel CPUs, and the last two with AMD CPUs. I bought the extra two computers because I've managed to find an extra two people to work at my company, and AMD-based PCs are cheaper so I've decided to buy them instead of Intel.
Long-story short, I've installed Ubuntu 9.10 and boot time takes about half-an-hour. After the computers finally boot, USB hardware doesn't work at all. I was forced to buy PS/2 keyboards & mice and they both work fine after the PCs boot.
I don't know what's causing this delay.
I've enabled Cool 'n Quiet from BIOS.
I've tried several instructions like editing the /etc/modules file.
I've installed cpufreqd, tried to configure it, but it didn't work.
I've check the CPU stats and my CPUs are running at 800MHz. 
I can't believe nobody managed to fix the 800MHz problem as I've noticed it's quite common among AMD Ubuntu users. 
I think I've tried almost anything that I've found on this forum.
I can't keep asking my employees not to reboot their PCs. Both Chrome/Firefox crash a lot on Ubuntu so they're forced to restart their computers.
The computer specs are: AMD Athlon II X2 240 dual-core @ 2.800MHz, 2GB RAM, 500GB HDD, etc.
I've been patient, but now I can't stand it anymore.
I'm open to suggestions. Thanks in advance.

---

### Post by Joe of loath on 2011-03-21
Have you tried the computers on a newer version of Ubuntu, like 10.04 or 10.10? That would be your first port of call, since 9.10 only has a month of support left.

---

### Post by desperatenoob on 2011-03-21
> **Joe of loath said:**
> Have you tried the computers on a newer version of Ubuntu, like 10.04 or 10.10? That would be your first port of call, since 9.10 only has a month of support left.

Sorry, I forgot to mention that I've updated both PCs to Ubuntu 10.04.

---

### Post by Jerry N on 2011-03-21
What brand of motherboard are you using?  My Gigabyte motherboards with AMD processors work just fine with although my old single core Athlon 2400+ boots a little slow - it takes bit over a minute.  Has anyone tried to "tweak" the BIOS settings for better performance?  I ask this because I have had to work on computers that have been rendered inoperable by computer tweakers.  Do you get any messages while the computer is trying to boot?  Can you tell if it really takes that long to boot or is it continually restarting until it finally works?  

Jerry

Couple more questions:  Why did you enable Cool n Quiet?
Any chance you changed the AHCI settings?

---

### Post by desperatenoob on 2011-03-21
> **Jerry N said:**
> What brand of motherboard are you using?  My Gigabyte motherboards with AMD processors work just fine with although my old single core Athlon 2400+ boots a little slow - it takes bit over a minute.  Has anyone tried to "tweak" the BIOS settings for better performance?  I ask this because I have had to work on computers that have been rendered inoperable by computer tweakers.  Do you get any messages while the computer is trying to boot?  Can you tell if it really takes that long to boot or is it continually restarting until it finally works?  

Jerry

Couple more questions:  Why did you enable Cool n Quiet?
Any chance you changed the AHCI settings?

I've enabled Cool 'n Quiet because this was recommended in all threads I've seen. I didn't change anything else. Before that it was set to "Auto" so it probably enabled itself when booting.

The motherboard is ASRock with AM3 support: asrock n68c-se.

---

### Post by cascade9 on 2011-03-22
You shouldnt have to install CPUfeq, it should be enabled by default. 

Since you are talking about the '800MHz problem' I'd guess that CPUfreq is running. BTW, 800MHZ is NOT a 'problem', that is what the modern AMD CPUs downclock to at low loads to reduce heat output and power requirements.

Well, its not a problem unless it refuses to clock up atloads anyway, which cant recall ever hearing about without there being a problem.... 

No USB, now that is a problem (probably not connected to CPUfreq though). Chrome browser, I wont say anything about that apart from I avoid proprietary software if there is a perfectly good open source program that does the same thing. Firefox shouldnt crash like that though, and that might be connected to your very slow booting time. 

I've used a asrock N68-S UCC/AMD 4800+/2GB DDR2, the same basic board as the N68C-SE (just no DDR3 support, and AM2+ not AM3). Its a crap board, but it takes far, far less time to boot than your does, with less CPU power and (probably) slower RAM and HDD. Its well under a minute to boot to KDE4.X, not ubuntu though. Unless you are doing somethign nasty like running DDR2 and DDR3 at the same time (IIRC the N68C-SE has DDR2 and DDR3 slots) then I have no idea why it is taking so long to boot. 

I'd try installing bootchart and seeing if it gives you any hints as to what I taking so long.

---

### Post by desperatenoob on 2011-03-23
> **cascade9 said:**
> You shouldnt have to install CPUfeq, it should be enabled by default. 

Since you are talking about the '800MHz problem' I'd guess that CPUfreq is running. BTW, 800MHZ is NOT a 'problem', that is what the modern AMD CPUs downclock to at low loads to reduce heat output and power requirements.

Well, its not a problem unless it refuses to clock up atloads anyway, which cant recall ever hearing about without there being a problem.... 

No USB, now that is a problem (probably not connected to CPUfreq though). Chrome browser, I wont say anything about that apart from I avoid proprietary software if there is a perfectly good open source program that does the same thing. Firefox shouldnt crash like that though, and that might be connected to your very slow booting time. 

I've used a asrock N68-S UCC/AMD 4800+/2GB DDR2, the same basic board as the N68C-SE (just no DDR3 support, and AM2+ not AM3). Its a crap board, but it takes far, far less time to boot than your does, with less CPU power and (probably) slower RAM and HDD. Its well under a minute to boot to KDE4.X, not ubuntu though. Unless you are doing somethign nasty like running DDR2 and DDR3 at the same time (IIRC the N68C-SE has DDR2 and DDR3 slots) then I have no idea why it is taking so long to boot. 

I'd try installing bootchart and seeing if it gives you any hints as to what I taking so long.

I don't understand why it takes so long. I don't think I've mixed up DDR2 with DDR3 as I haven't messed with its internals. 

The USB thing might be related to this 800MHz "problem." 

What bothers me is that if I install something or change the /etc/modules file or some other file, upon the first restart, boot takes ~2 minutes. If I restart the PC again or shut it down then turn it back on, then the boot time goes back to ~30 minutes.

I'll install bootchart and maybe I'll find something wrong.

---

### Post by mcduck on 2011-03-23
> **desperatenoob said:**
> I don't understand why it takes so long. I don't think I've mixed up DDR2 with DDR3 as I haven't messed with its internals. 

The USB thing might be related to this 800MHz "problem." 

What bothers me is that if I install something or change the /etc/modules file or some other file, upon the first restart, boot takes ~2 minutes. If I restart the PC again or shut it down then turn it back on, then the boot time goes back to ~30 minutes.

I'll install bootchart and maybe I'll find something wrong.

Still, what "800 MHz problem". :D

Every modern processor switches to lower frequency when there's not much work for it to do.

Have you checked the frequency when the computer is actually doing some CPU-intensive task? If it doesn't scale to full speed then, *that* would e a problem.

Also even if it wouldn't scale correctly, booting up at 800MHz wouldn't slow the boot process that much, and wouldn't cause you any problems with USB devices. So it's clearly something else that's causing your problems.

You might want to post the bootchart here when you got one. And  also a bit more information about what edits you have done/tried doing to the modules etc...

---

### Post by desperatenoob on 2011-03-23
> **mcduck said:**
> Still, what "800 MHz problem". :D

Every modern processor switches to lower frequency when there's not much work for it to do.

Have you checked the frequency when the computer is actually doing some CPU-intensive task? If it doesn't scale to full speed then, *that* would e a problem.

Also even if it wouldn't scale correctly, booting up at 800MHz wouldn't slow the boot process that much, and wouldn't cause you any problems with USB devices. So it's clearly something else that's causing your problems.

You might want to post the bootchart here when you got one. And  also a bit more information about what edits you have done/tried doing to the modules etc...

I've tried this: [http://ubuntuforums.org/showthread.php?t=1307021](http://ubuntuforums.org/showthread.php?t=1307021)

And this: [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

In the /etc/modules I've added 3 new lines, but I can't remember exactly and I can't remember exactly what lines I've added... it was something like: "....-k8" "....userspace"

I'll try to check the RAM. A bootchart log is coming ASAP.

---

### Post by desperatenoob on 2011-03-23
After installing bootchart, the computers boots really fast. What did bootchart trigger? I've rebooted twice just to make sure.

EDIT: Images were resized. Is there a way I could prevent this from happening?

---

