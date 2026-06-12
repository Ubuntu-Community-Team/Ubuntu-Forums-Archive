---
title: "Ubuntu 10.10 Keeps Freezing. Help Please."
date: 2011-02-27
forum: General Help
---

### Post by drewsus on 2011-02-27
Hello, UF

So, Ubuntu 10.10 on my desktop has been freezing quite frequently. 

The PC:
Intel Core Duo CPU @ 2.66GHz
2GB RAM
Nvidia GeForce 9500 GT w/ 1GB RAM 
[INDENT]driver version 270.18[/INDENT]
Kernel 2.6.35-24-generic

It will "randomly" lock up when I doing various tasks and the only thing that works is a press of the reset button or ALT+PRTSCN+R+E+I+S+U+B, but sometimes that doesn't even work. 

How can we diagnose this? 
Thanks in advance, 
dRewsus

---

### Post by drewsus on 2011-02-28
*bump* 
There has to be someone that can help me here

---

### Post by Dobbie03 on 2011-03-12
I am having the same issue as you except nothing works other than holding down the power button.

---

### Post by coldcut on 2011-03-16
same problem here!

i3 540
nVidia 9800GTX+
4gb ram

---

### Post by r.osmanov on 2011-03-16
I had the same problem. And struggled a lot to find out something in logs. There were something not obvious in Xorg logs... 

Then I found a damaged capacitor on video card. Just it was actual issue :) Replaced the card, and had no problems any more.

**EDIT:** Heh, I had the same video card

---

### Post by r.osmanov on 2011-03-16
I'd also minimized startup items e.g. via **rcconf**. Some time ago gwibber run crazy with 100% CPU load.. Don't know what it was, but I've removed it in Ubuntu 10.04. But as since Maverick it seems OK.

Good luck.

---

### Post by Sina_RJ on 2011-03-16
can you tell what is the last thing you do when your system got hang?
I had this problem when i move my mouse over docky or panels!
can you explain more?
and what applications you got that is related to video stuff?

---

### Post by drewsus on 2011-04-10
> **Sina_RJ said:**
> can you tell what is the last thing you do when your system got hang?
I had this problem when i move my mouse over docky or panels!
can you explain more?
and what applications you got that is related to video stuff?

It seems like it can happen at any time, but it seems to be when closing a video in FFox (be it flash/mplayer) but not always. Seems to happen when doing something with totem/mplayer as well. And sometimes when opening Rhythmbox. I multitask a lot so its hard to know exactly what is doing it at any given time. 

I suppose I can see about replacing the gfx card, but I dont have a lot of $ to throw around at the moment (just splurged on some Games Workshop stuff and building a new tank for my python).

PS- I have tried various versions of Nvidia Drivers. My initial post stated the use of a beta driver, and then I reverted to a more current driver (260.19.36 or something from some PPA) and am now back to 260.19.06 from the default repos)

---

### Post by tpost001 on 2011-04-14
Ubuntu 10.10 freezing up on me is really frustrating.  I thought it was from FireFox but it happens in Chromium, too.  I think I know now what is happening and can explain the previous writer.  It seems that when it happens to me it is always when I am minimizing a window or switching to another one.  I can see the shrinking or growing outline of the window and then it freezes and I have the artifact of the window outline on my screen.  Usually all I can do is power off the computer.  CTRL-ALT-DEL sometimes brings up a Shut down window, and if that pops up, I can recover from the freeze.  But usually I have to power off and start up again.  Log sheets have shown me nothing, as I fear the logging abruptly stops when the computer freezes.  I have a Compaq desktop with an AMD Athlon 64 Processor 3300+, 1.8 GB RAM, and am up to date with Ubuntu 10.10.  The freezing happens in the 32-bit and 64-bit versions of Ubuntu.  I have Ubuntu 10.10 running successfully 5 other computers all installed from the same Live CD, so I am assuming it is a hardware issue.  I recently started all over from scratch with a new /home directory and it still freezes up.  Since it happens when I minimize windows (this does not happen every time, but at least 3-4 times a day) I think it may be an X- incompatibility with my hardware.

This is my lspci:

thomas@compaq:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:08.0 USB Controller: NEC Corporation USB (rev 41)
00:08.1 USB Controller: NEC Corporation USB (rev 41)
00:08.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


I do not have COMPIZ running nor do I have "Visual Effects" turned on.

Anyone have any ideas?

---

### Post by spirit.986 on 2011-04-14
I was also having a problem with freezing when i first installed ubuntu...
It was a specific freeze in a way that **everything was on a halt except the current window i was working on.** Nothing was working except that i was able to switch between the desktops with CTRL+ALT+Left/Right. The computer was at that state for about 3-5min and after that i would have get nervous and start to press all of the keys on my keyboard with my both hands... and that was causing a release... i didn't know how or what or why.. :)

Then i realized that the freez was caused by me while** I was suddenly touching the touchpad when working something and that was causing some sort of a CLICK LOCK on the touchpad**.. After that i installed a program called** [COLOR=Red]Touchpad-Indicator [/COLOR]**and it had the option to enable/disable the touchpad with a shourtcut... That was the solution of my problem..
[B]
ANOTHER SIMILAR PROBLEM.................................[/B]
Also i have to mention that on one of my older version of Ubuntu's i don't remember which was it.. the whole system was crashing when i was moving a the window on which a video has been playing.. for example moving the VLC Player window which is currently playing a video... that problem is gone on the Maverick version...

---

### Post by tpost001 on 2011-04-14
I will try the CTRL-ALT left or right combination next time it freezes.  Since I have a Desktop I don't have a touchpad.  But I am wondering if it could now be mouse related.  Mine freezes up without a video clip running.  But I would need to use the mouse to get a window to minimize.

---

### Post by drewsus on 2011-04-18
thank you for the input spirit, but those issues are not the same as mine. 
Furthermore, I couldnt confirm if this was Ubuntu specific or hardware til now. Some people were suggestion I have maybe a faulty graphics card or something. But, I have just spent some time in Windows 7 on the very same computer and have not had a single freeze. But how do I know? Well, I had the computer in W7 for like 2 steady days playing Dawn of War 2. Thats a little more system demanding than Firefox/Videos/Music. Ubuntu would have definitely crashed/froze in that time. 
I wish I could get the game going with WINE so I could see it freeze in Ubuntu, but that is another story. 
I wish I could just get a message telling me what halted the system...

---

### Post by akshunj on 2011-04-18
How long from boot till you get the freeze?

---

### Post by sam81 on 2011-04-18
this is going to sound a bit gross, I had serious random crashes (sometimes it would not crash for one, two days, but then it would just crash randomly again) as well on my PC, Q6600 with ubuntu, debian, sabayon and opensuse too, I spent endless time try to figure out what the problem was by looking at log files, running memtest and stress tests, until one day I opened up the computer case, and found that it had accumulated lots of dust inside, I hoovered it and now I have no more random crashes!

---

### Post by DukeBoxer on 2011-04-18
I was having similar problems with 10.10 crashing and couldn't figure out what was causing it. I got it to stop for a little bit by purging the nouveau drivers but then it started again. Then I installed 11.04 with ACPI=off as a boot parameter and no more problems! If I go into grub at startup and turn on ACPI then I get a lockup within minutes. Try holding down shift when you start the computer again, and then hit "e" on your kernel to edit the boot line where it says "quiet splash" and add ACPI=off to it and see if that helps. If it does, add it permanently to your /etc/defaults/grub menu and then do sudo update-grub. If not then install 11.04

---

### Post by drewsus on 2011-04-19
@akshunj
It seems to be somewhat random. I really can't pinpoint exactly what is causing it when it happens. It can happen within an hour of boot, or 11. 

@sam81
I cleaned it not too long ago (PSU fan, CPU fan, etc as well), but good suggestion

@DukeBoxer
I will try that, thanks!

---

### Post by this_costs_more_cell_bill on 2011-06-10
If some of you guys have Western Digital hard-drives, then you might be interested doing this:

sudo nano /etc/default/grub
and add:
 GRUB_CMDLINE_LINUX="libata.force=8.00:noncq"
 then update grub:
 sudo update-grub


..and no more freezing in the summer:popcorn:

---

### Post by drewsus on 2011-06-10
Ill have to try this when I get to Toronto and report back. THat should be Sunday. 
So what exactly is this doing and why do I need to do this with one of the most popular HDD brands around?

---

