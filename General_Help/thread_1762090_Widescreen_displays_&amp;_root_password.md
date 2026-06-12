---
title: "Widescreen displays &amp; root password"
date: 2011-05-18
forum: General Help
---

### Post by trevtoo on 2011-05-18
Hi, I've just installed 10.04 under VBOX, and need a bit of help to start off please.
1. I have an Acer Aspire One which has a 1024x600 display. Can I change the resolution from 800x600? A screen that small needs all the real estate you can find. I found the command 'xrandr', but that only lists 640x480 as an alternative. there must be o lot of users with wide screen displays, is everyone forced to standard 4x3  display?
2. What is the root password?
Thanks in advance,
Trev

---

### Post by wildmanne39 on 2011-05-18
> **trevtoo said:**
> Hi, I've just installed 10.04 under VBOX, and need a bit of help to start off please.
1. I have an Acer Aspire One which has a 1024x600 display. Can I change the resolution from 800x600? A screen that small needs all the real estate you can find. I found the command 'xrandr', but that only lists 640x480 as an alternative. there must be o lot of users with wide screen displays, is everyone forced to standard 4x3  display?
2. What is the root password?
Thanks in advance,
Trev
Hi, for the most part all you need is your user password, or in other words the password you used when you setup ubuntu. You borrow root previlages when need in a terminal by using the sudo before all commands then put in your password. You need to go to virtualbox.org and read there manual it will tell you what you need to know. On there site you can download extension pack that can fix your display problem, and you can make your screen full size, then if you need help come and ask your questions. :p

---

### Post by trevtoo on 2011-05-19
Hi. Tks for the password info. My question about full screen is about the linux desktop. I am in VBox full screen display, but my Linux desktop is only 800X600 on a 1024X600 PC screen. Need to be able to expand that to fill the entire screen. Like I said the command xrandr will show me my options, but that isnt one of them. Is there a way of adding that option by editing a file?
BTW, I'm new to this forum. A couple of times ago I stumbled across something which allowed me to find my posts, instead of scrolling through the lot, now I can't find it again. Can U help please. Maybe a PM.
Thanks
Trev

---

### Post by aphatak on 2011-05-19
The first thing I would try is the easy way - see if you can set the resolution in 'System -> Preferences -> Monitors'.  If the resolution you want is listed in the Resolutions drop-down list, you are home and dry.  Select it, click 'Apply', then confirm you want to keep the new resolution and that is it.

If you don't see what you want in the dropdown box, gird yourself for a bit of work.  Check if a proprietary driver is available for your hardware - this is likely if you have an ATI / NVidia chip.  If one is available, you will find it under System -> Administration -> Additional Drivers.  If you find a graphics driver for your hardware, activate it (you will have to restart to complete the activation), and try the System -> Preferences -> Monitors again.

If this doesn't work, be prepared to use the command line.  You will have to define a new mode, and include it in your X-configuration.  This forum is not the reight place to give a complete description of the process;  however, you will find a pretty good description at "https://wiki.ubuntu.com/X/Config/Resolution".

I have two requests of you -
[LIST=1][*]Give this a try, and post the results in this thread.  Your efforts, whether you find a solution you like or not, will help other members with similar problems.
[*]When you find a solution (please note - I am not saying 'if'), mark this thread as SOLVED.  In addition to helping people with similar problems, people will not keep proposing solutions afterwards.
[/LIST]

---

### Post by trevtoo on 2011-05-19
Hi, think I've sort of worked it out. It may have actually been VBox issues from the start. I bought myself an 8GB USB stick and ran it from there. Came up full screen straight away.
thanks for all the replies. May call this one [SOLVED]
Trev

---

