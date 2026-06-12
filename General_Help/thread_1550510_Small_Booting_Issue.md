---
title: "Small Booting Issue"
date: 2010-08-11
forum: General Help
---

### Post by Tycho59 on 2010-08-11
I'm having small boot issue with my present Linux box, which is presently  running Ubuntu 8.04 LTS.  When booting from a Live CD, Ubuntu 9.xx+ or any other linux variant I have, the machine will come to a complete stop about half way into the boot process.  I think this may have something to do with the WiFi card that I have installed.  Are there any suggestions that could help me remedy this problem short of removing the card itself??

Much thanks in advance.

Tycho

---

### Post by nidzo732 on 2010-08-11
Did you check the integrity of the cd.There is an option when booting from the cd.What CPU are you using how much ram you have.

---

### Post by Tycho59 on 2010-08-11
The system has a 3.2 GHz P4 & 1GB of ram. I had been able to boot from a live CD with no problem before adding the wireless card, but now it just seems to get stuck or stall. The Live CDs i have are fine. I've even run a lens cleaner in the drive n still i have the same issue.

---

### Post by Tycho59 on 2010-08-11
If it matters any, the WiFi Card I'm using is a TRENDnet Wireless TEW-423PI.

---

### Post by varunendra on 2010-08-12
While booting, press 'shift' key to bring up advance boot menu. There, press F6 and check the following:

> acpi=off
noapic
nolapic
nomodeset

If this allows you to boot successfully, then perhaps you need to look for a proprietary driver for your WiFi card.

---

### Post by Tycho59 on 2010-08-13
I tried as you suggested, but nothing happened.  For proprietary drivers, if you mean the drivers that came with the card, I already have those installed.

---

### Post by varunendra on 2010-08-15
As per your first post-
> **Tycho59 said:**
> I'm having small boot issue with my present Linux box, which is presently  running Ubuntu 8.04 LTS.  When booting from a Live CD, Ubuntu 9.xx+ or any other linux variant I have, the machine will come to a complete stop about half way into the boot process.
I assume that the driver you've installed is in 8.04 LTS, and the other versions you are trying only with live CDs not a native installation. If so, then the installed driver has nothing to do with LiveCD environment.

A few questions:

[LIST=1]
[*]Have you tried booting without the card installed? If not, do it now & post here how it goes.
[*]Did the driver CD have a driver for linux? If not, then how did you install the driver? ([ndiswrapper]("http://ubuntuforums.org/showthread.php?t=400258")?)
[*]Which variants have you tried so far? If not already tried, I'd suggest [Mint9]("http://www.linuxmint.com/download.php") (may serve as permanent OS) or [Slax]("http://www.slax.org/") (just to see if it succeeds to boot **with** the card).
[*]Have you tried the same options I told in my earlier post with 9.10? Try them now if you already haven't.
[/LIST]
If the computer can boot & run successfully without the card, then I'd suggest to make a native installation of Karmik or Lucid in a separate partition (dual boot). Once it is installed & running fine, then install the card again and try to boot & see how it goes.

---

### Post by Tycho59 on 2010-08-17
I've tried ubuntu 9.10 & 10.04 as well as mint 9 & all of them have the same issue. No problem booting with out the card installed. I've set it up as a dual boot for now.

---

### Post by varunendra on 2010-08-17
I googled for linux/ubuntu + TRENDnet Wireless TEW-423PI related issues but none of the results were like yours (not even able to boot!).

Besides, a review on amazon.com said it worked 'out-of-box' with linux (distro/ver. wasn't mentioned). On the forums also there are many threads that say it worked out-of-box with [Intrepid Ibex]("http://old-releases.ubuntu.com/releases/intrepid/") (e.g. [this]("http://ubuntuforums.org/showthread.php?t=978032") & [this]("http://ubuntuforums.org/showthread.php?t=968468")) or with [ndiswrapper]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page") (other versions) but none had the boot problem.

I'm sure you also must have already come across the above search results, and that's why I was suggesting Slax. Based on knoppix and geared towards optimized networking experience, maybe it can give us some positive results.
Due to uniqueness of your problem, I'm also suspicious about a hardware combination issue (like weak PSU, a defect causing power-overdraw, a possible conflict during boot-time configuration of network interfaces, et.). But these may be meaningless if you are able to boot & work flawlessly with another OS.

By the way, what are your current dual boot OSes? Are they both working without issues with the card installed?

---

### Post by Tycho59 on 2010-08-17
I have my machine dual booting 8.04 Hardy Heron & 10.04 Lucid Lynx.  After setting up dual boot, installing the cards drivers n updates, everything seems to be working just fine now,

---

