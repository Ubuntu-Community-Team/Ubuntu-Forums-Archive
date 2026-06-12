---
title: "Ubuntu ~ Would 64bit release solve my freezing issues?"
date: 2012-04-23
forum: General Help
---

### Post by Hylas de Niall on 2012-04-23
Hi again!

Over the last year i've become enamoured with Unity and really really want to use it on my desktop machine, but i have been having issues running anything using the 3.xx.x kernels (not just the Ubu's). I have had repeated 'lock-outs' and freezes necessitating hard reboots every time.

I have submitted numerous times the spec of my machine (which i will do again later this post) and checked the memory using memtest. All my hardware seems good, and I have no issues running earlier Ubu's (currently 10.04.4) and Windows 7 (32bit and 64bit) under pretty heavy workloads, but with the recent Ubuntu's (11.10 and 12.04) it has had this issue.

**The machine itself came pre-installed with Win 7 (home premium) 64bit**, which, in a fit of rebellion i wiped (I have a legitimate 'off the shelf' licenced - ie, not OEM - copy of Win 7 which i use as a fall-back) in favour of Linux.

The Ubu's i have been having issues with are the 'default' 32bit versions, and i guess my question is: Would i be better off installing the dedicated 64bit version of Ubuntu?

As i understood it, and as the Ubuntu site seems to indicate, the 32bit (default?) version should be fine - well... *it doesn't seem to be* in the case of my hardware.

I ran the check mentioned here:  [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)  and it *does* return 'lm' as a flag (twice - i guess once for each core) so, would 64bit be better? I thought the PAE kernel resolved any issues 32/64bit.

Here's my hardware specs:

**Acer Aspire AX3812**
CPU: Intel Core 2 Duo 2.7GHz
MEMORY: 3Gb DDR2-400
CHIPSET: Intel P45/G45, 199MHz fsb
Graphics and Audio all on-board.

I really want to be riding that Pangolin on this machine, but i don't want to go through another install only to have the same issue with the 64bit version.

Can anybody help me on this? 

TIA, Hy

---

### Post by oldos2er on 2012-04-23
What type of graphics? Intel?

---

### Post by Hylas de Niall on 2012-04-23
> **oldos2er said:**
> What type of graphics? Intel?


Yep. GMA AX4500.

There don't appear to be any 'additional drivers' for this, though i understand it's supported directly in the kernel?



here's the machine i have issues using recent Ubu's on: [http://www.acerdirect.co.uk/Grade_A1_-_Acer_Aspire_AX3812_Dual_Core_Desktop_PC__A1-98.H7M7Z.UYN/version.asp](http://www.acerdirect.co.uk/Grade_A1_-_Acer_Aspire_AX3812_Dual_Core_Desktop_PC__A1-98.H7M7Z.UYN/version.asp)

---

### Post by gordintoronto on 2012-04-23
Cute machine, but it might not have enough airflow. How long does it run from a cold state before it freezes? (The machine you linked to has a Celeron processor, which generates less heat than a real Core 2 duo.) Can you play youtube videos?

The Linux kernel has used more CPU, generating higher temperatures, over the past couple of years.

If it were my machine, I would install lm-sensors, then run: sudo sensors-detect answering "yes" to every question, reboot, run: sensors and see what temperatures are reported. 

Install conky and an appropriate script, and you could see the temperatures all the time.

With 3 GB of memory, you shouldn't even need the PAE kernel. 32-bit should be fine, I would not expect an improvement with 64-bit. If you've got a spare flash drive, you could always try it.

---

### Post by techsupport on 2012-04-23
Download 12.04 LTS 64-bit migrate that ISO to a USB Flash Drive and boot from that Flash Drive. Leave it running overnight to see the results. Keep an eye on the temp specs.  And if you are happy with the results install 12.04 from the Flash Drive you made.

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

> **Hylas de Niall said:**
> Hi again!

Over the last year i've become enamoured with Unity and really really want to use it on my desktop machine, but i have been having issues running anything using the 3.xx.x kernels (not just the Ubu's). I have had repeated 'lock-outs' and freezes necessitating hard reboots every time.

I have submitted numerous times the spec of my machine (which i will do again later this post) and checked the memory using memtest. All my hardware seems good, and I have no issues running earlier Ubu's (currently 10.04.4) and Windows 7 (32bit and 64bit) under pretty heavy workloads, but with the recent Ubuntu's (11.10 and 12.04) it has had this issue.

**The machine itself came pre-installed with Win 7 (home premium) 64bit**, which, in a fit of rebellion i wiped (I have a legitimate 'off the shelf' licenced - ie, not OEM - copy of Win 7 which i use as a fall-back) in favour of Linux.

The Ubu's i have been having issues with are the 'default' 32bit versions, and i guess my question is: Would i be better off installing the dedicated 64bit version of Ubuntu?

As i understood it, and as the Ubuntu site seems to indicate, the 32bit (default?) version should be fine - well... *it doesn't seem to be* in the case of my hardware.

I ran the check mentioned here:  [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)  and it *does* return 'lm' as a flag (twice - i guess once for each core) so, would 64bit be better? I thought the PAE kernel resolved any issues 32/64bit.

Here's my hardware specs:

**Acer Aspire AX3812**
CPU: Intel Core 2 Duo 2.7GHz
MEMORY: 3Gb DDR2-400
CHIPSET: Intel P45/G45, 199MHz fsb
Graphics and Audio all on-board.

I really want to be riding that Pangolin on this machine, but i don't want to go through another install only to have the same issue with the 64bit version.

Can anybody help me on this? 

TIA, Hy

---

### Post by oldos2er on 2012-04-24
> **Hylas de Niall said:**
> Yep. GMA AX4500.

There don't appear to be any 'additional drivers' for this, though i understand it's supported directly in the kernel?


Right, Intel video drivers are open source.

If I had to guess, I'd say that this might be the cause of the freezing. See [http://en.wikipedia.org/wiki/Intel_GMA#Linux](http://en.wikipedia.org/wiki/Intel_GMA#Linux)

---

### Post by Hylas de Niall on 2012-04-24
> **gordintoronto said:**
> Cute machine, but it might not have enough airflow. How long does it run from a cold state before it freezes? (The machine you linked to has a Celeron processor, which generates less heat than a real Core 2 duo.) Can you play youtube videos?

The Linux kernel has used more CPU, generating higher temperatures, over the past couple of years.

If it were my machine, I would install lm-sensors, then run: sudo sensors-detect answering "yes" to every question, reboot, run: sensors and see what temperatures are reported. 

Install conky and an appropriate script, and you could see the temperatures all the time.

With 3 GB of memory, you shouldn't even need the PAE kernel. 32-bit should be fine, I would not expect an improvement with 64-bit. If you've got a spare flash drive, you could always try it.

It's a nice little machine, but low power and low profile, so i can't get a plug-in gfx card for it! (i did purchase the recommended Asus EA4350 'silent' low profile gfx card for it, but due to the location of the mobo slots and the size of the heatsink on the card it physically wouldn't fit!).

How long before a freeze? Well, that would vary from time to time. Sometimes it would be as little as twenty minutes, whilst other times it could be a few hours before a lock-up, and sometimes not at all.

I have no problems playing youtube videos or running games (Sauerbraten, Open Arena etc), and under Win7 it can happily run GTA 3, GTA Vice City, GTA San Andreas, Need For Speed 'Most Wanted', and Far Cry without issues. Also in Win7 i run Ableton Live and Sony Acid (the latter being the only real reason i still have a Windows boot option at all).In fact it has *never* locked up in Win7 either 32 or 64bit.

I do a fair bit of web browsing (firefox 11) and photo manipulation and processing (GIMP) - both from the SC and not ppa's, and it's usually during or just after using these that the locks occurred - strangely never (so far) during or after gaming or watching videos.

I don't hear any extra fan noise before a freeze so i never considered it was an overheat problem, although other than that it does seem to indicate that. *Something* is having to work too hard.

I think i will install the 64bit version, take your advice and install the lm sensors and conky (is the std version in repos good enough?) and keep an eye on things that way...

Thank you for your help! :)

---

### Post by Hylas de Niall on 2012-04-24
> **oldos2er said:**
> Right, Intel video drivers are open source.

If I had to guess, I'd say that this might be the cause of the freezing. See [http://en.wikipedia.org/wiki/Intel_GMA#Linux](http://en.wikipedia.org/wiki/Intel_GMA#Linux)

Hmm. Could well be, as 12.04 (and 11.10 before it) run fine on my gma500 netbook, (Medion Akoya mini e1210 - basically a rebranded MSI Wind U100) not even forcing me to use _2d_ Unity!

Thank you for your help :)

---

### Post by Hylas de Niall on 2012-04-24
> **techsupport said:**
> Download 12.04 LTS 64-bit migrate that ISO to a USB Flash Drive and boot from that Flash Drive. Leave it running overnight to see the results. Keep an eye on the temp specs.  And if you are happy with the results install 12.04 from the Flash Drive you made.

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Good idea and thank you for the link. I will try this prior to installing.

---

### Post by oldos2er on 2012-04-24
Here's some more info on Intel GMA500: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by TBABill on 2012-04-24
Other users who experienced random freezing found it was some sort of conflict with Banshee. Removing it fixed system-wide freezes, but I don't have further details to assist. Wondering if a quick uninstall of Banshee would be worth trying since it can be easily added back?

---

### Post by Hylas de Niall on 2012-04-24
> **TBABill said:**
> Other users who experienced random freezing found it was some sort of conflict with Banshee. Removing it fixed system-wide freezes, but I don't have further details to assist. Wondering if a quick uninstall of Banshee would be worth trying since it can be easily added back?

Banshee isn't in Precise though... It's back to Rhythmbox :)
I only use Audacious anyway :)


I think i may try that asus graphics card - chop up the case so its heatsink sticks out the top. That should certainly eradicate any issues with graphics  ...or add some new ones ;)

---

### Post by Hylas de Niall on 2012-04-24
Woah!

Right now i'm running the 64bit daily build (23rd April) from a usb stick as advised, and boy is it fast! I'd say it matched my 10.04.4 install for speed right now.

Can *such* a performance leap be just down to it running from flash memory as opposed to HDD  ---or is it because it's the 64bit version?

I dug out an old 80gig hard drive that i was going to install it to for testing .....but now i'm really tempted to bang it onto a spare partition on the existing setup.

I think i should go for an install of this for two reasons:

1. The software that i typically used on the setups that locked me out  other than Firefox, isn't preinstalled on the daily build (and there is no persistence on this usb booter) so i can't really get a comparable test this way.

2. This is just *so blazingly fast* compared to running Oneiric and previous dailies and the betas of Precise from usb sticks that i'm convinced there must have been some sort of issue with my system running the 32bit version. I really can't accept that such a huge performance increase can have happened in just the last couple of days.

Seriously. I'm **astounded** at the difference here. I know 64bit is really for folk with over 4gigs of RAM, but it seems that a 64bit OS on 64bit architecture *will* show a perfomance increase over PAE too:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

I seem to be seeing this right now --or has the build *really* improved that much that fast?

I don't know whether to be apprehensive or ecstatic! LOL!

(plus, i decided against the GFX card in the end. It would have made too much of a mess of the case, and it is after all a dreaded ATI under that asus badge)

---

### Post by Hylas de Niall on 2012-04-26
> **gordintoronto said:**
> Install conky and an appropriate script, and you could see the temperatures all the time.

With 3 GB of memory, you shouldn't even need the PAE kernel. 32-bit should be fine, I would not expect an improvement with 64-bit. If you've got a spare flash drive, you could always try it.

I've installed the 64bit version and it rockets along on my machine! :D
Clearly something is working better, whether it's due to last-minute 'fixes' to Ubu as a whole or because it's the 64bit version i don't know, but right now i'm *very happy with it* indeed!

As far as Conky goes ...well, it's a whole new ball-game for me. I have installed the conky-std but have no idea at all what to do with it as far as running it from boot-up and configuring what is displayed on-screen with .rc scripts. I had a quick look through the two main conky threads on here, but those were more concerned with the scripts and i couldn't find anything about running it. I tried a quick gooogle as well, but i'm still at a loss. Could you point me to any 'noob-centric' sites that may enlighten me?

Many thanks,

Hy

---

### Post by Hylas de Niall on 2012-04-26
Aw crap!

I spoke too soon, just had my first freeze up. I've had enough of this, my desktop pooter clearly isn't up to the task of running these later kernels - whatever the flavour of distro, so it's back to Debian Squeeze for me.

Gonna mark thread as 'solved' because the answer is clearly a resounding 'No'.

I'm gutted :(

But i'll keep it on the laptop as long as it plays nicely.

---

### Post by davidvandoren on 2012-04-26
go into your BIOS and disable your on board audio.

Then either try your install and see or better reinstall and see if it freezes. 

I had freezes and all kinds of problems with my pc as well. No matter which version I used it crashed from time to time. After disabling the Audio the problem disappeared over 6 weeks now. Not a single crash or freeze.

---

### Post by Hylas de Niall on 2012-04-26
> **davidvandoren said:**
> go into your BIOS and disable your on board audio.

Then either try your install and see or better reinstall and see if it freezes. 

I had freezes and all kinds of problems with my pc as well. No matter which version I used it crashed from time to time. After disabling the Audio the problem disappeared over 6 weeks now. Not a single crash or freeze.


No good - i need audio. It's a done deal now anyway ;)

---

