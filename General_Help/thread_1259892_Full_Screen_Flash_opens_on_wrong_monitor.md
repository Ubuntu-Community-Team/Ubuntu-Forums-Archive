---
title: "Full Screen Flash opens on wrong monitor"
date: 2009-09-06
forum: General Help
---

### Post by snipazer on 2009-09-06
Hey, so I have Ubuntu 9.04 x86. Flash is installed and works fine. Problem is, whenever I go into full screen mode with youtube, hulu, etc videos, they open on the wrong monitor. I have two monitors on my Nvidia 8800GT. My right monitor is my main monitor and whenever I go into full screen, it opens on the left monitor. Can I change where it opens up to? Thanks a bunch

---

### Post by ranzy on 2009-09-12
I have the exact same question. I play farmtown on facebook. I open firefox on the right monitor, then click full screen on the game it opens on the laptop (left) monitor.

---

### Post by miltiad on 2009-10-30
I have the same problem on Ubuntu 9.10 64 bits. 

Nvidia driver provided by Ubuntu (185) two monitor (one on each videocard in SLI).

I'm setup with twinview.

---

### Post by jandrioli on 2009-12-02
Nothing?
This is still happening on ubuntu 9.10 x86, Nvidia drivers version 185.18.36, twinview with compositing via compiz.

So my "default" (main) screen is on the left (laptop's monitor) and the huge dell screen on the right. When I try to get flash on fullscreen from the right monitor, it shows on the left one.

---

### Post by scouser73 on 2009-12-02
If you want the larger monitor to be the primary monitor then you'll need to follow my instructions below.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish the login screen to appear

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by jandrioli on 2009-12-02
> **scouser73 said:**
> If you want the larger monitor to be the primary monitor then you'll need to follow my instructions below.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish the login screen to appear

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

scouser73, this is totally unrelated to the issue man ;)
anyway, u guys need to vote on adobe's bug tracking system to fix this bug in flash player: [http://bugs.adobe.com/jira/browse/FP-562](http://bugs.adobe.com/jira/browse/FP-562)
as of now there's only 19 votes there :(

---

### Post by miltiad on 2009-12-02
Just voted.

---

### Post by djreep81 on 2009-12-09
Hey guys, i have a decent work around.  Note that the screen that will accept the full screen is always the screen on the left.  it always looks for 0,0 to start the full screen in flash.

In Ubuntu, to system -> preferences -> display.  

The display preferences will pop up.  Make sure if using nvidia, you turn off your driver (just make sure NVIDIA X Server Settings does not pop up)

You should see a screen with the available monitors
The trick here is to "drag" the monitor that you want to see the flash player full screen in to the left side of the other.  (making it 0,0 location)

It worked for me and i was having the same issue.  It is a work around until adobe makes a fix.  Knowing how quickly they get to there bugs, you may be doing this for a while

---

### Post by Julianz on 2010-11-11
I have the same problem. None of the suggestions worked of me. 
It does not seem to me like problem with flash. Any program that goes into full screen mode opens the screen at my PC monitor (and not my second monitor from which the program was launched). 

For example, when opening a open office presentation in my second monitor (TV) and hitting the full screen option it also opens the full screen in my PC monitor.
One of the main reasons I bought a digital TV was to connect it to my PC and watch flash movies. Without the nvidia driver I got it to work but I need the driver to have a proper resolution. So it looks to me that the problem is with the driver.

---

### Post by nossifer on 2011-01-15
Same.  Still not sure how to get flash videos to open onto the same window I am currently using (second monitor)

---

