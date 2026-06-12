---
title: "Maverick: sometimes very slow, mouse lags, low cpu load"
date: 2010-11-10
forum: General Help
---

### Post by m4lte on 2010-11-10
Hi there,

Since I upgraded to Maverick, every now and then (maybe once an hour) my system becomes very slow for about half a minute. The mouse cursor reacts only very slowly and also applications freeze for for some time.
This happens without the CPU being on full load or the hard disk being active.

I made a clean ubuntu installation on a new hard drive a week ago, but the problem persists.

I have a Thinkpad R400 with an Intel GMA 4500 graphics card an an Intel T5670 Core 2 Duo processor. I'm running the most up to date stable version of ubuntu. Kernel 2.6.35-22.

I know the description of the problem is very vague, but it's hard to describe it more accurately. I couldn't find anything helpful on google or the forum. If you have any ideas what might cause the problem or which log files might provide useful information, please let me know. Most importantly, the problem did not occur before I upgraded to Maverick.

cheers!

---

### Post by lmarmisa on 2010-11-10
Have you checked the screensaver and power management options?. Try to deactivate the sleep options and change the "Regard the computer as idle after" 2 hours and check if the frequence of the problem changes. This is only an idea.

Good luck!.

---

### Post by vi.zanquini on 2011-02-06
bump!

EXACTLY the same problem.
Also updated my kernel to the latest version, and the problem persists.
Running on a desktop here, though
P7P55D-PRO Motherboard
i7 860 processor
Mouse is PS/2 and Keyboard is USB

Thanks in advance for anyone who provides an answer for us :)

---

### Post by Shocker on 2011-02-19
Same problem here since, at least, 2 ubuntu versions...

In my case this issue happens most of the times when I'm downloading files with full ADSL2+ bandwidth (900 KBps min).

I initially thought it was related to my keyboard and mouse battery charge (and people laughed at me...:
[http://ubuntuforums.org/showthread.php?t=1401928](http://ubuntuforums.org/showthread.php?t=1401928)

Nowadays, since I bought a new PC (apart keyb and mouse), I horrified seeing that again... 

My system is now composed as follows:

mobo: ASUS P7P55 LX
CPU: Intel i5-750 
RAM: 8 GB
Video card: Nvidia GTX460 by Palit (1024 MB of RAM, PCI-E)
network: eth0 integrated + 1 spare PCI card
Mouse + keyboard: Logitech EX110 wireless desktop - now completely USB connected 
Other usb devices:HP Printer,3D connexion SpaceNavigator

OS.: Ubuntu 10.10 64bit with all the latest updates

Maybe it's an IRQ related issue? How can I check if everything is ok on that side?

Any hint is greatly appreciated!

Bye

Shocker

P.S.:It seems this problem like this keep raising day by day:

[http://askubuntu.com/questions/19202/mouse-and-keyboard-freeze](http://askubuntu.com/questions/19202/mouse-and-keyboard-freeze)
[http://ubuntuforums.org/showthread.php?t=1423346](http://ubuntuforums.org/showthread.php?t=1423346)
[http://serverfault.com/questions/78972/why-ubuntu-is-slow-on-massive-network-disk-i-o](http://serverfault.com/questions/78972/why-ubuntu-is-slow-on-massive-network-disk-i-o)

I will give a try to the proposed solutions in the meantime...

---

### Post by Shocker on 2011-02-22
Other info:

I found a page with large download file to test connection speed 

[http://www.thinkbroadband.com/download.html](http://www.thinkbroadband.com/download.html)

I've been checking my system with them. each time I started the download (through firefox or Chrome or wget) the mouse start moving like crap and I found difficult even to left click (the button was like kept pressed so i.e I was starting dragging a firefox tabs instead of closing it...)

Please anyone willing to help please give it a try too and confirm if it only my system...

a) I edited the grub start-up command as indicated in:

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

but no better behavior - mouse still laggy at the same time I start to download at full bandwidth

b) I tried the same with windows 7 64bit home premium. No good news. I then pressed the MemOK button to reset and optimize the RAM setting on my mobo and then saved the settings in the bios at the next reboot. 

c) Then I booted the UBUNTU DVD 10.10. I could download at more than 900 KBps without any mouse issue

d) When I rebooted ubuntu, I noticed that this time the downloads did not interfere with the mouse signals. 

As you can see things are not clear at all at the moment...
I tried to look into the event logs but I actually lost myself in the many different files (dmesg/messages/kernel etc.) 
Is there anyone experiencing the same issue and being trying to solve it?

Please help!

Shocker

---

### Post by Shocker on 2011-02-23
I finally understood is just a problem of interferences.

Just try this test and see what happens:

as soon as you start havin the lag issues on the your mouse movements, simply touch the receiver.
In my experience everything turned to work perfectly! :)

This seems to be a known issue of some R/F desktops:

[http://forums.logitech.com/t5/G-series-Gaming-Mice/Logitech-G7-High-Network-Latency-Causes-Mouse-Lag/m-p/285863](http://forums.logitech.com/t5/G-series-Gaming-Mice/Logitech-G7-High-Network-Latency-Causes-Mouse-Lag/m-p/285863)

Moreover this evening I understood that the PS/2 cable connection is not needed (and may give interferences) if the other one is connected to a USB port.

Bye everybody 

Shocker

---

