---
title: "Ubuntu 12.04 freezing completely!"
date: 2012-06-10
forum: General Help
---

### Post by oslub on 2012-06-10
I am currently using Ubuntu 12.04 and for the second time in a week,  Ubuntu freezes completely, becoming entirely unresponsive. The only way  to use it again is to turn off the power to reboot.


  Both times the same thing happened. All of the sudden, the wireless  connection to the Internet is lost, ubuntu keeps trying to connect and  asks for password and some seconds later then it freezes. 


I don't understand why the wireless connection fails, since it works  fine after I reboot PC and I am close enough to router, I never had  wireless problem on Windows 7 for example. I also do not understand why this loss of connection implies ubuntu freeze.



  This is a serious issue because I have no chance of saving work. This time I couldn't save some edits I was doing on a document...

---

### Post by sanderj on 2012-06-10
Is the 12.04 fully updated and upgraded?

If so: was an earlier version of Ubuntu working stable? If so, why not use that version?

---

### Post by oslub on 2012-06-10
Yes it is fully updated...

I installed 12.04 from scratch, it is not upgraded from a previous version. Besides, since this is a LTS release, I would like to keep it, but first I need to solve this trouble.

The problem is I don't know how to recreate this situation in order to provide some more information. It just happens without warning and all of the sudden.

---

### Post by little_penguin on 2012-06-10
It might be a video or hardware related issue. What hardware are you running it on? Is it a desktop with a dedicated graphics card (eg. Nvidia) that supports 3D, or does it use shared onboard graphics as in many laptops or netbooks? My netbook, for example, used to freeze if I used the default Unity, but it's okay under Unity 2D. You can log out and select the Unity 2D session at the login screen. Try the 2D version and see if it helps. Alternatively, try one of the plainer Gnome session alternatives (without any special graphic effects).

---

### Post by oslub on 2012-06-10
I run Ubuntu 12.04 on a Toshiba Laptop,  Pentium(R) Dual-Core CPU T4300  @ 2.10GHz 2100 MHz, 4GB RAM, , Intel Mobile 4 Series Chipset Integrated Graphics Controller. It supports Unity 3D, as I already checked with 

/usr/lib/nux/unity_support_test -p

Unity 3D supported:       yes

The wireless device is this:
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller
Realtek WLAN controller

Yes the graphics controller is onboard, although it supports Unity 3D. I'll try the Unity 2D as you say, or even another desktop environment, but anyway, any ideas on why this only happens following a strange, unexpected loss of wireless connection and not in any other circumstances?

---

### Post by oslub on 2012-06-10
Since I have 3D support on my graphics controller, should I file a bug report to launchpad?

---

### Post by little_penguin on 2012-06-11
You could, but perhaps the 3D graphics isn't the culprit, it is just one possibility. Does the total freezing stop when you use Unity 2D?

---

### Post by oslub on 2012-06-11
> **little_penguin said:**
> You could, but perhaps the 3D graphics isn't the culprit, it is just one possibility. Does the total freezing stop when you use Unity 2D?

I have switched to Unity 2D, I can't tell right now if it stops the problem because the freeze happened twice last week, so it can take 2 or 3 days to happen again I guess.

I will now wait a few days using unity 2D and see if something happens.

---

### Post by oslub on 2012-06-15
I've tried to replicate this occurence by turning off my wireless router, but no freeze has happened. So far I was unable to recriate this situation, which is making it more difficult to predict when it will happen, what causes it and how to solve... Anyone already experienced something similar before, so I can have an idea of where the conflict may be coming from?

---

### Post by paulusms on 2012-06-17
Hi there, 

My Ubuntu 12.04 64bit freezes too.

The system I'm using is:
Intel Core-i5 3750K
Gigabyte Z77-DS3H
no additional graphic or sound

I have not yet found out what is causing the freeze. Sometimes I go a day without one, today it froze like every f***ing hour. 
I'm not doing anything special - today mainly surfing the web.

Installation from scratch.
All updates installed.

I'm going to check for Bios updates now....

---

### Post by mastablasta on 2012-06-18
did you check:
 
- CPU temperature (might be good to do some cleaning inside) ;-)
- motherboard to see if any capacitors are bulger

---

### Post by oslub on 2012-06-22
> **paulusms said:**
> 

I have not yet found out what is causing the freeze. Sometimes I go a day without one, today it froze like every f***ing hour. 
I'm not doing anything special - today mainly surfing the web.

Installation from scratch.
All updates installed.

I'm going to check for Bios updates now....

Exactly the same thing with me, I also can't find the cause for this, I can't even recreate the problem myself and also have all updates and installed 12.04 from scratch, except I don't usually get freezes as often as you do, as I started this topic, I had about 2 or 3 per week. The fact that it happens suddenly and doesn't allow me to save opened tabs and work is very uncomfortable.

I believe it may have something to do with Unity effects though... I've made a question about this at launchpad but no luck at the moment.

---

### Post by oslub on 2012-06-22
> **mastablasta said:**
> did you check:
 
- CPU temperature (might be good to do some cleaning inside) ;-)
- motherboard to see if any capacitors are bulger

None of those seem to be the problem so far...

I can see that this is an issue that may have several causes in its origin, it is difficult to diagnose.

Personally I actually like Unity and already got used to it, I know that probably changing interface would prevent the crashes but that wouldn't be exactly solving the problem, it is important to understand what is causing this in order to fix it for future releases, as there are more users complaining about the same.

---

### Post by paulusms on 2012-06-29
BIOS Update didn't help.

> Originally Posted by **mastablasta** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12036148#post12036148") 				
 				[I]did you check:
 
- CPU temperature (might be good to do some cleaning inside) :wink:
- motherboard to see if any capacitors are bulger[/I]

Temperature is fine (34°C)
Capacitors are fine too.

Very annoying is, that I couldn't pinpoint the problem... 
At least one positive sideeffect: I do save my stuff quite regularly now :)

---

### Post by Carborundum on 2012-06-29
> **paulusms said:**
> Hi there, 

My Ubuntu 12.04 64bit freezes too.

The system I'm using is:
Intel Core-i5 3750K
Gigabyte Z77-DS3H
no additional graphic or sound

I have not yet found out what is causing the freeze. Sometimes I go a day without one, today it froze like every f***ing hour. 
I'm not doing anything special - today mainly surfing the web.

Installation from scratch.
All updates installed.

I'm going to check for Bios updates now....
This is a known issue with Ivy Bridge graphics. It's fixed in kernel 3.3.6.

Since the OP isn't using an Ivy Bridge graphics adapter, their problem is most likely not related.

---

### Post by oslub on 2012-07-22
Updating the information about my experience with Ubuntu for the last three weeks, I did not have any freezes, but the sudden loss of the wireless connection still is happening from time to time and requires reboot to become functional again. It is a Realtek Wireless LAN Module provided for Toshiba laptops.

I can see that there is a lot of people experiencing much more frequent and serious crashes than me, I believe this is mostly due to Unity effects and Graphics Cards by NVIDIA. I may have less problems because I have no proprietary drivers on my system, my Graphics controller is Intel onboard and it supports Unity 3D. Still, something is messing with the wireless device and sometimes that is followed by a complete system freeze.

Anyway I have decided to give a try on a different interface to eventually arrive to some conclusions, I like Unity just fine and as I said before, changing to another interface is not really solving the issue, but I will run Lubuntu from the hard drive as a triple-boot for a while and see what happens.

---

### Post by florentnicoulaud on 2012-10-10
I am experiencing quite the same issue.
My system completely freezees and it seems to be related to a connection loss.
My coworkers and I are connected to the same switch and it appears that they are losing the network connection when I experience the system freeze. They are not using Linux and are not subject to the freeze. I am using Ubuntu 12.04 with gnome shell.
I haven't found anything in the system's logs.
My only lead is the network connection loss.

My system is fully updated.
Computer is a Lenovo Thinkcenter  M91p.
Cpu is an Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
Integrated Graphics Controller

---

### Post by Kristof A on 2012-11-20
I have same issue with Xubuntu 12.04. Regular (at least once a week) system freezes with nothing in the logs... Use a Dell e6410 (Intel I5).

---

### Post by Rebelli0us on 2012-11-20
> **paulusms said:**
> Hi there, 

My Ubuntu 12.04 64bit freezes too.

The system I'm using is:
Intel Core-i5 3750K
Gigabyte Z77-DS3H
no additional graphic or sound

I have not yet found out what is causing the freeze. Sometimes I go a day without one, today it froze like every f***ing hour. 
I'm not doing anything special - today mainly surfing the web.

Installation from scratch.
All updates installed.

I'm going to check for Bios updates now....

My Z77 had random crashes, installing the latest Linux kernel fixed the problem.

---

### Post by nir2000 on 2012-12-10
Hi!
My Ubuntu 12.04 freezes up as well.
It did not happened in previous LTS version.
I'm using AMD and an on board graphic.
Please help to solve this problem.
Nir

---

### Post by abrianb on 2012-12-28
See if this sounds like the problem...
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

---

### Post by thesoothsayer on 2013-01-19
Having these freezes for a long time now.

Screen freezes along with the mouse and keyboard, and takes no inputs, but ssh works. Can still hear audio if I'm playing a song or movie. However, nothing I do can unfreeze the screen. The only thing I can do is to restart via ssh.

Completely at a lost as it's random, and I can't find anything in the logs. 

This ia a dual-boot machine with windows 7, and windows has never hung before even if I leave it on days at a time (although I don't use it that often).

---

### Post by 026rus on 2013-03-27
I have the same problem and it look like it happens when I watch videos in browser.

---

### Post by UncleAsriel on 2013-05-02
I am another person with an instance of this problem.

While having multiple browser tabs (5 to 10) in Firefox, the screen becomes unresponsive but the the mouse can still be moved.  

Another incident involving VLC player convinced me that the video freezing was related to the graphics card. While freezing all video and accessibility in mid-video, the audio continued to play.

I tried attempting to bring up the terminal, or the 'super-terminal' called up by Ctrl + Alt + F2, but neither input appears to work. A hard reset is the only method I can manage to get the system back up and running.  

I am consider attempting [this method]("http://lenss.nl/2012/10/workaround-ubuntu-12-04-mysterious-system-freezes/"), but as a beginner Linux user, I'm unfamiliar with the command line basics and don't want top monkey with things I do not understand.

Can someone advise?


[ATTACH]242117[/ATTACH]I

---

### Post by Broco on 2013-05-31
UncleAsriel, I think this isn't the same issue.
We are talking about complete freezes, no mouse movement, no nothing.

Got the same issue here:
64bit system
All updates installed
Kernel: Linux 3.2.0-40-generic
Graphic card: ATI Radeon HD5570 - newest drivers installed (including catalyst control center), had the same issue with fglrx
Mainboard: Asus P8H67V (newest firmware installed)
8GB Ram
2 HDDs (1TB and 500G)

Freezes for no apparent reason, sometimes it's just fine, sometimes not.
Cannot even REISUB when it freezes so I think it's a kernel issue.
Log files don't show a hint due to the kernel stopping on freeze.

---

