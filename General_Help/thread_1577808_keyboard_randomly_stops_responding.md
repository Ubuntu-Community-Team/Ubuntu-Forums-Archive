---
title: "keyboard randomly stops responding"
date: 2010-09-19
forum: General Help
---

### Post by lizard_b on 2010-09-19
Hi forumn, I've been experiencing seemingly random keyboard lockups in lucid lynx 10.04.  I am fairly certain than it is not a hardware problem, since when I dual boot into windows it never happens.  This has happened since I installed ubuntu on this (new) machine.  I am using the proprietary ATI driver.

The symptoms:
Eventually, the keyboard stops responding to input.  I think that it always happens while I am using the keyboard, but can't say for sure.  Many times, the last key struck repeats into any input it can.  It could be the case that that always happens, and it is sometimes an invisible key like ctr alt or shift.  The mouse always works, and if there isn't interference from a repeating key I can use the screen keyboard.  

Hitting capslock does not make the light come on.  My keyboard has an f-lock key, and hitting it does not enable the function keys.  alt-sysreq-r does not appear to fix it, alt-sysreq-h does not give me output, and ctr-alt-f1 does not bring a terminal up.  alt-sysreq-k does not appear to work, but sometimes it makes the screen lock up.  Rebooting makes it go away.  Looking at the usual error logs after reboot does not show anything suspicous to me.


There have been many similar reports in many versions of ubuntu in the forums and launchpad, most of which go away spontaneously after a major upgrade (or downgrade, or the person stops using ubuntu) or receive no followup.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253740)
[http://wwww.ubuntuforums.org/showthread.php?t=1561839](http://wwww.ubuntuforums.org/showthread.php?t=1561839)
[https://bugs.launchpad.net/ubuntu/+bug/195805](https://bugs.launchpad.net/ubuntu/+bug/195805)
[http://ubuntuforums.org/showthread.php?t=347682](http://ubuntuforums.org/showthread.php?t=347682)
[https://wiki.ubuntu.com/X/Troubleshooting/HalBreaksKeyboardAndMouse](https://wiki.ubuntu.com/X/Troubleshooting/HalBreaksKeyboardAndMouse)

I have no idea what (if anything) triggers the problem, so I don't know how to reproduce it.  Sometimes it will go days or a week without happening, sometimes 10 minutes.

Can anyone suggest what the problem might be, or a potential workaround?  If you have an idea, what logs should I be looking at to verify?

---

### Post by lcayton on 2010-10-25
I'm having the identical problem.  It is incredibly annoying, as it interrupts my work at least daily.  

I'm on 10.04.  The keyboard I'm using is NOT usb, but I'm almost positive the keyboard is fine (I've tried swapping).  It seems to usually happen in emacs, but this is not surprising as I do 90+% of my work in emacs.

I cannot use the keyboard at all when this occurs, but the mouse still works.

---

### Post by vanBuuren on 2011-01-02
I also am having this problem. Sometimes the keyboard stops responding at all. Caps Lock und Num Lock leds don't respond anymore, the keyboard is completely dead. The mouse still works.

Some days it does not happen at all, however today it already happened twice. It indeed is very annoying.

I am using ubuntu 10.10 with an old ps/2 Keyboard. I am however almost certain the keyboard cannot be the issue. It used to work without any problems on an older computer with ubuntu 8.10.

Do you guys still experience these problems or (and how) have you been able to resolve them? Thanks.

---

### Post by lcayton on 2011-01-06
I still have this problem.

---

### Post by SidZ on 2011-01-06
[COLOR=DarkSlateBlue]I have this problem as well. I have posted a thread so I will keep you guys updated if I get lucky.

What kind of computer and keyboard models do you guys have?[/COLOR]

---

### Post by lcayton on 2011-01-07
Can you give us a link to the other thread?

I'm on a intel i5 system.   The choice of keyboard doesn't seem to matter too much ... the one I'm using now is branded "Cherry", which is some inexpensive german-made thing.  

The only slightly unusual part of my system is the Nvidia GPU.

thanks

---

### Post by vanBuuren on 2011-01-07
For completeness I will give my system configuration:

[LIST]
[*]Motherboard: Asus P7P55D
[*]CPU: Intel core i5 650
[*]PSU: Antec EarthWatts EA430D Green
[*]Memory: Kingston HyperX 2x2GB DDR3 1600 Mhz
[*]Videocard: ASUS ENGT240 SILENT/DI/1GD3 (Nvidia GForce GT240)
[*]HD 1: Corsair Force Series F60 (60 GB - intern - 2.5" - SATA-300)
[*]HD 2: Seagate Barracuda 7200.12 (TB - intern - 3.5" - SATA-300 - 7200 rpm - buffer: 32 MB)
[*] Keyboard: PS/2, can't find a brand but is has served me very well over the past years
[*] Mouse: I have no mouse, but use a Wacom Intuos 4 S drawing tablet(USB connected) instead
[/LIST]

This all running on Ubuntu 10.10 x64.

---

### Post by alligoodw on 2011-01-07
I have the same problem.  I'm not sure what I'm gonna do!  I hope someone finds the solution soon.  I'm using an Acer laptop as well.

---

### Post by lcayton on 2011-01-10
A bit moire info about my system, since it appears quite similar to vanBuuren's:

Motherboard: ASUS P7P55D-E
CPU: Intel core i5 750, 2.67Ghz
Nvidia GTX285.

Someone else at my work has been experiencing the same problem.  Her computer is identical except for the graphics card, which is not an nvidia.

---

### Post by alligoodw on 2011-01-10
> **alligoodw said:**
> I have the same problem.  I'm not sure what I'm gonna do!  I hope someone finds the solution soon.  I'm using an Acer laptop as well.

I've made a decision.  

After having difficulties with the keyboard over several Linux distributions installed, I've decided that the problem is the keyboard itself.  I've return the laptop, still under warranty, to the manufacturer for repair.  

Regardless the operating system, I had the keyboard to freeze and I observed a behavior where it appeared that I was holding down a key continually, when in fact, I wasn't. 

Yes!  I cleaned the keyboard thoroughly.

---

### Post by vanBuuren on 2011-01-29
I think I have resolved the problem.

Haven't had keyboards freezes since I got my  [Filco Majestouch]("http://www.keyboardco.com/keyboard_details.asp?PRODUCT=623"). The keyboard is working perfectly to my satisfaction, not cheap though.

I guess the latest Ubuntu release somehow does not fully support some older keyboards, so trying out a newer keyboard might resolve the issue.

---

### Post by OnSite511 on 2011-01-31
I just got the latest update and now my keyboard is dead in my primary login. Fortunately I set up root to have a gnome login and I'm able to use the keyboard (this message is proof). I guess I need to find out what the latest update(s) were....

---

### Post by lcayton on 2011-02-06
I switched to a new USB keyboard and the problem seems to have gone away.  I'm pretty sure the old keyboard was functioning correctly, so I guess there is some problem between the keyboard, the ps/2 port, ubuntu, and god knows what else..

---

