---
title: "Ubuntu 11.10 freezing constantly"
date: 2011-11-22
forum: General Help
---

### Post by bardu on 2011-11-22
After todays (Nov. 22) updates my 64bit NVidia Ubuntu box is freezing already for the fourth time. Anyone else with the same issue?

---

### Post by [Neurotic] on 2011-11-22
My 11.10 installation (also nvidia, and 64bit) has been freezing constantly ever since I upgraded to 11.10, and it's driving me nuts.

I was actually about to post a note asking if anyone else has had the same symptoms.

Here is my bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/893431](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/893431)

Although I'm sure there are more.

Are you able to move your mouse or anything when it freezes (I can't)? Can you SSH into the box when it freezes (I can't do that either).

Basically, it's reboot, and continue on.

I'm seriously under whelmed with this release of Ubuntu.

---

### Post by bardu on 2011-11-22
Sometimes I can move the mouse, sometimes not. But this is all I could do except a hard reboot.

And yes, I notice freezes since upgrading to 11.10, but not so often as of today.

---

### Post by collisionystm on 2011-11-22
I would guess it is a driver problem.
I had the same issue when I was using catalyst 11.10. It was having problems with OpenGL under Unity/Gnome-Shell. Even things such as the Global menu bar were eating up CPU usage.
I suggest trying the official nvidia driver and seeing if that clears things up for you

---

### Post by [Neurotic] on 2011-11-22
> **collisionystm said:**
> I suggest trying the official nvidia driver and seeing if that clears things up for you

Is there another driver to use?

Noveau doesn't support 3D, so you can't even use it with Unity, except the 2D version :P

Or do you mean, go to the Nvidia site, and download the latest? If so, you can grab it from the proposed changes repository, as I have done (and it didn't help).

---

### Post by [Neurotic] on 2011-11-23
Just had a quick question for you all -

How many of you with freezing problems are running more than 1 monitor?

Thinking back to when I first install 11.10, I was only using 1 monitor, and didn't have much in the way of freezes. Wondering if it's a multi-monitor thing?

---

### Post by oldtimer7777 on 2011-11-23
Are you using two same standard monitors or is this a basketcase where you have two different make/models running at the same time?

> **'[Neurotic] said:**
> Just had a quick question for you all -

How many of you with freezing problems are running more than 1 monitor?

Thinking back to when I first install 11.10, I was only using 1 monitor, and didn't have much in the way of freezes. Wondering if it's a multi-monitor thing?

---

### Post by [Neurotic] on 2011-11-23
I'm running my laptop monitor (alienware m17x, r1) and a dell 24" screen as well.

> **oldtimer7777 said:**
> Are you using two same standard monitors or is this a basketcase where you have two different make/models running at the same time?

---

### Post by Bobhuber on 2011-11-23
> **bardu said:**
> After todays (Nov. 22) updates my 64bit NVidia Ubuntu box is freezing already for the fourth time. Anyone else with the same issue?
I just tried updating the Nvidia drivers (from their site) today from 285.05.09 to 290.10 and immediately ran into problems with gnome-system-monitor pushing one of my CPU's to 100% and freezing the program. I went back to the earlier driver and all is well again.
11.10 Gnome3

---

### Post by [Neurotic] on 2011-11-23
Yeah, I'm running GeForce GTX 280M, using Unity, on driver 285.05.09.

When/if(?) I crash next, I'm going to try and switch over to Gnome Shell, and see if that is any more stable.

---

### Post by oldtimer7777 on 2011-11-23
> **'[Neurotic] said:**
> Yeah, I'm running GeForce GTX 280M, using Unity, on driver 285.05.09.

When/if(?) I crash next, I'm going to try and switch over to Gnome Shell, and see if that is any more stable.

Disable compiz compositing and see if that stops it from happening for now.

---

### Post by FWBeck on 2011-11-28
I've been having the same issue with Ubuntu 10.10, 11.04, and now with 11.10; always 64-bit desktop edition.

[LIST]
[*]AMD Athlon 64 X2 on Asus M2N32-SLI Deluxe motherboard, 4 GB DDR2 RAM
[*]2 × 120 GB SATA hard drives stripe set on onboard NVIDIA SATA RAID controller
[*]Ubuntu 11.10 64-bit Desktop with latest updates
[*]ATI Radeon HD4350 512 MB on PCIexpress with ATI proprietary driver
[*]22" BenQ monitor on HDMI output, NEC VT770 projector on DVI output; VGA output not used
[*]Onboard 802.11g wireless network adapter connected to internet via wireless NAT router
[*]Plenty of heat dissipation: CPU fan, power supply fan, 5 case fans
[/LIST]The system is running two applications with relatively moderate performance demand: OpenLP for projecting song lyrics to the projector, and Audacity in the background for recording live speech from the PA mixer.
 
After about 1½ hours the mouse pointer freezes, and the system becomes unresponsive. The monitor and Projector continue to display what was on-screen when the system froze up. No response to any mouse or keyboard input, also no response to a shut-down command from short-pressing the power button.
 
After restarting the system, the same freeze occurs, but already after a few minutes.
 
At this point, I cannot begin to guess which hardware/software combination might be causing the trouble.
 
If anyone knows of a solution, I would be grateful. If I can't get this to work, I may need to resort to trying a different Linux distribution or even Windows.

---

### Post by [Neurotic] on 2011-12-04
I've just switched back to nouveau for now. It was either that or start rolling back through nvidia drivers to find a stable one...

---

### Post by ibrrfarr on 2011-12-05
Brand New Computer and Install (See:  [http://ubuntuforums.org/showthread.php?p=11515248#post11515248](http://ubuntuforums.org/showthread.php?p=11515248#post11515248) ).  I have NO frills or needless programs installed.  Would be nice to get something done here.  :confused:

---

### Post by johnnybravos on 2011-12-17
j

---

### Post by 14quartz on 2012-02-11
[FONT=Comic Sans MS][SIZE=4][FONT=Verdana]I too face the same freezing problem. I'm using using dell XPS 15(using optimus technology). Always hard [/FONT][FONT=Verdana][SIZE=3]booting[/SIZE][/FONT][FONT=Verdana] :(

Still No solution for this.:(
[/FONT][FONT=Verdana]
[/FONT][/SIZE][/FONT]

---

### Post by stptrx on 2012-03-18
This looks like an old thread but most appropriate (outside of a closed mouse pointer freezing thread which seemed very relegated to laptops) 

I have not been able to get any type of log files. 

I have however found one consistency in that USB Devices seem to be conflicting if I am not reading too far into things. 

I read in the other thread that the issue seems to happen on either a laptop and seems to be conflicting with the touchpad and mouse pointer. 
-another post mentioned a bluetooth dongle however 

I also have been experiening a great number of issues with freezing. sometimes complete other times it was random inaccuracy with mouse pointer and a "seemingly" unresponsive system. 

I have found however that once I unplugged my wacomb tablet the issues cleared up. 

THis issue is similar in both installed Ubuntu Studio and running "Live" Dream Studio

I am currently using nvidia drivers on a 64bit amd based machine. (since that seems to be of possible interest on this thread)

I am wondering if anyone can confirm removing unnecessary HID or other USB related devices clears up this issue. 

Really Need to be able to have wacomb tablet readily accessible at the end of the day, just figured getting this confirmed may help get to the root of the issue.  
Thank you.

---

### Post by Ravi5kumar on 2012-04-17
I have the same problem in Ubuntu 11.10. Hope they will fix it in 12.04):P!

---

