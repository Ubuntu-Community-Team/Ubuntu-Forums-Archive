---
title: "Hibernate not working in 11.04"
date: 2011-04-28
forum: General Help
---

### Post by Kreeyon on 2011-04-28
I've just installed Ubuntu 11.04 on my Acer Aspire One D260 netbook.   Everything works fine apart from Hibernate.  

The netbook will go into hibernate without any problems at all, but when I switch the netbook back on Ubuntu loads up with distorted multi coloured graphics and then freezes.

---

### Post by Linxguy on 2011-04-28
I have given up on Ubuntu. 10.10 worked for a while until the sound stopped working. In 11.04 my wireless usb adapter doesn't work at all. Linux Mint works fine.

---

### Post by Gazz1e on 2011-04-29
Same issue here. I've spent a couple of hours recreating my swap partition, still no good. I've gone back to 10.04.

---

### Post by Kreeyon on 2011-04-29
Cannot figure out why Hibernate does this and scrambles the graphics upon booting up.  Suspend doesn't do this and works perfectly.

---

### Post by snideatlondon on 2011-04-29
same problem here (Acer Aspire 533) but overall I quite like 11.04 actually. definitely an improvement on 10.10

---

### Post by jmprUF on 2011-04-30
> **snideatlondon said:**
> same problem here (Acer Aspire 533) but overall I quite like 11.04 actually. definitely an improvement on 10.10

Dito, same problem on Toshiba NB305. No other problems noted with 11.04.

---

### Post by datgs on 2011-05-01
The same problem with my Lenono G400 :-s. When I back with previous hibernate, the screen was in black. The machine is running still I guess but I cound't see anything.

Which keys is used to open the terminal my situation?

---

### Post by BSD_dad on 2011-05-02
+1 Toshiba NB305. Return from hibernate I get the right 20% of the screen works fine (full vertical) rest of screen black with some hash/snow at top 20%.

---

### Post by minglis on 2011-05-03
Dell Studio 1758 doesn't hibernate either. With 10.10, it used to work ONLY if I manually selected hibernate from the menu, rather than just closing the lid. When it came back, the colours would be all weird for a while, then it would eventually start back up. With 11.04, it never fully shut down. I selected to hibernate, then it closed everything and just stayed on a black screen (still powered on though).

---

### Post by Gazz1e on 2011-05-04
Still not got hibernate working on my Acer Aspire A150. According to some forums, the fault may lie in the kernel and it could take a while for a fix to be released. Some people said the natty betas had similar hibernate issues. Not sure how much truth is in that.

Last night I installed 11.04 on my wife's ageing Gateway laptop (>4 years old). Hibernate works fine. 

I expect the issue is due to a graphic card driver.

---

### Post by wallyhall on 2011-05-06
Same issue on Advent 4211-B.

lspci output is:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

```

---

### Post by matt_symes on 2011-05-06
Hi

What graphics cards are you guys using ?

```
lspci -nnk | grep -iA2 vga
```

Is there any commonality there ?

Kind regards

---

### Post by werewolves on 2011-05-06
> **minglis said:**
> With 11.04, it never fully shut down. I selected to hibernate, then it closed everything and just stayed on a black screen (still powered on though).

Same here on Sys76 Daru2.

---

### Post by astowe32 on 2011-05-06
Same problem here with black & hit or miss wake from sleep.
HP Netbook 2105.
lspci output:
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: Hewlett-Packard Company Device [103c:3660]
	Kernel driver in use: i915

---

### Post by datgs on 2011-05-07
Hi all,

I've tried to use the older version of linuz, no problem with hibernating.

---

### Post by kingkookie on 2011-05-09
Greetings,

I am experiencing the same issue.  Oddly, after I wake from hibernate, then click on Suspend and wake again, well, at least it fixes the graphics.  Not really a fix, though.

lspci output:
```
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by mehrdad.j on 2011-05-10
Same problem here, When my samsung netbook wakes up from hibernate, there is a black rectangle covering 70% of login screen, in the same time there are some strange coloured pixels writen on this area. When I blind click on login window, it is possible to login and as before the desktop is covered but everything else is working fine, even the compiz. 
I tried to open the terminal with CTRL+ALT+F1 but it also adds more random pixels to this rectangle. The workaround of additional suspend after each hibernate wakeup worked for me.

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
    Subsystem: Samsung Electronics Co Ltd Device [144d:c072]
    Kernel driver in use: i915
:confused:

**[COLOR=Blue]UPDATE: If I let my netbook to have more time before I try to login , I mean as long as the screen saver starts to run, then the mouse move will clear that black area and I can login and nothing is wrong. I hope this will also help you guys. it works for me[/COLOR]**

---

### Post by matt_symes on 2011-05-10
Hi

So you all have an intel graphics cards and you are all using the i915 graphics driver ?

Kind regards

---

### Post by colinvv on 2011-05-11
Yes, i915 driver on Lenovo IdeaPad S10-3t does not return from hibernate properly.

---

### Post by AlGreen500 on 2011-05-12
I get the 3/4 blank screen on return from hibernate too.
i915 on Acer Aspire One AOA150 ZG5

---

### Post by tanzantj on 2011-05-13
Same here. Asus EEE PC 1005 HA.

:~$ lspci -nnk | grep -iA2 vga

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
    Kernel driver in use: i915

Pain in my a.  But at least the 20% on the right side works so i"m able to open a terminal and "sudo reboot".

---

### Post by Sami Lehtinen on 2011-05-14
Same problem here, but I think it's more hibernating than recovering that isn't working. With my system hibernating happens way too fast to actually do anything useful. It takes less than three seconds. So it's pretty clear that ram isn't being stored to disk properly.

---

### Post by Frankiewizard on 2011-05-16
Well I can't help any one with this problem because I have not moved to 11.04 yet. But with 10.10 & a AsuS 701 hibernate & Suspend works wonderfully well.

Good luck.

---

### Post by Sonsum on 2011-05-17
Anybody else seeing the commonality? I have this issue too on my Samsung Netbook. And most of the reported issues are also on netbooks.

I'm going to take a guess that it is the intel integrated graphics card found in these that's to blame.

I'll keep you guys posted if I find anything.

---

### Post by matt_symes on 2011-05-17
Hi

Have you guys tried unloading the graphics driver during hibernating and reloading it during thawing as part of the hibernate process. That may fix it.

Kind regards

---

### Post by mehrdad.j on 2011-05-19
> **Frankiewizard said:**
> Well I can't help any one with this problem because I have not moved to 11.04 yet. But with 10.10 & a AsuS 701 hibernate & Suspend works wonderfully well.

Good luck.


You are smart. I just jumped in the newly released, and then found that its not LTS, Do you guys know of any way to go back to 10.10 cause "I see no important changes that worth staying on 11.04?

---

### Post by Sonsum on 2011-05-20
I downloaded the prereleased next kernel and the problem was fixed. It's just a matter of time until they officially release it and all will be well :)

---

### Post by samMD on 2011-05-20
lol its basically why would you need it when you have a 10 sec boot time..the devs obviously are focusing more on startup and shutdown..

---

### Post by jim_charlton on 2011-05-22
> **BSD_dad said:**
> +1 Toshiba NB305. Return from hibernate I get the right 20% of the screen works fine (full vertical) rest of screen black with some hash/snow at top 20%.

I have exactly the same situation on a Toshiba NB305.  It worked great on Maverick but started acting up on Natty.  Does not matter whether I boot tickless (nohz=0 highres=0) or not.

---

### Post by Soldier2580 on 2011-05-28
Same problem, different laptop. Packard Bell EasyNote LJ61. My screen goes black, power stays on, and I can't get to the log in screen or anything. 

Maybe switch back to 10.10 untill this is fixed?



EDIT: I've found [this article]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"), stating a hibernate problem in 10.10, is there anyone who can 'translate' what this article suggests doing? And is it similar to the problem here?

---

### Post by prentiz on 2011-06-07
Another person with the same problem, this time on my Aspire One ZG5, which has an Intel 945GME graphics controller.  Sometimes it hibernates OK, but most of the time waking from hibernation causes some sort of graphics error where the left half of the screen disappears into multi-coloured error.  It seems like every other Ubuntu update breaks my netbook...

---

### Post by Lidio1 on 2011-07-01
Acers in general seem to have screen issues, at least in my experience. 

When I was running Vista (<<< God help me...) on my Aspire 4315, some kind of short developed between the screen and the motherboard. On random occasions, and often during sign-off, the screen would go completely white and unresponsive. I had it fixed several times both under and off warranty, but the problem kept coming back. I learned to live with it though; the laptop would eventually go into sleep mode, then when I used the keyboard to wake it up, the screen would be fine.

I'm now running Ubuntu 11.04, and the problem persists; however, no matter which power settings I put it on, the laptop goes into suspension after about 1 minute, the screen remains white, the keyboard completely unresponsive. Closing the lid seems to make no difference whatsover. The only solution I've found is to hit the power button, which wakes the laptop, before immediately shutting it down.

I don't think I have ever witnessed this thing go into suspension/hibernation on it's own since I've loaded Ubuntu. I'm pretty certain it's just a power management issue. I'm a new user, so maybe somebody here knows something I don't. My current settings are as follows:

On A/C:
Lid closed - Suspend
Spin down hard disks when possible - CHECK

On Battery:
Lid closed - Suspend
Low Battery - Hibernate
Spin down hard disks when possible - CHECK

---

### Post by Bnelsonmiller on 2011-07-02
I have the same problem on my Acer netbook.

It sounds like the next kernel release will fix this problem. However, in the meantime, my solution is to avoid the hibernate function in favor of the shutdown.

---

### Post by Sami Lehtinen on 2011-10-14
I solved (or actually kind of worked around) hibernate not working issue by installing **uswsusp**. It seems to be working wonderfully on all computers this far. I had three systems where hibernate just lost the system state. After installing uswsusp, all of these are working. Two regular intel desktops and one HP (intel) laptop.

I'm sure there might be several reasons for hibernate not working, but luckily this helped with every system I had problems with.

---

