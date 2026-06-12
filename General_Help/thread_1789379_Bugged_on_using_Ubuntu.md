---
title: "Bugged on using Ubuntu"
date: 2011-06-23
forum: General Help
---

### Post by Spitfire777 on 2011-06-23
Hi,

please don't mind some mistakes in writing english, because i'm not a native english speaker, because I was looking in forums in my language for my bugs in Kubuntu and did not find solutions. And also please don't mind, if this post is something about critizsm in any ways.

I've been using Ubuntu for two years now and I really like to use it, because it's open and the opportunities are so massive. But now because of the bitter-real joke of unity desktop and after giving it a failed try, I've switched to Kubuntu. But many problems I had under Ubuntu, I have now on Kubuntu, too of course.

But very often I've got problems in the daily routine, where "normal" things do have to work, but they don't. Of course, Ubuntu is able to do more than Windows, but my opinion is that a modern OS does have to solve "normal" issues without using Google everytime and switching to the command prompt, customize config files in many cases for solving the problem. Well, after a fresh installation everything works yet, but if it comes to hardware support, special applications, etc. Ubuntu fails in many cases, what I can reproduce on various systems I have. My opionion is, that Ubuntu developers should work more on hardware support and reliability than working on **** (yes, S-H-I-T!) like Unity or other newer or "cooler" UIs.

My problems now and I hope you can help me, where the mistake is:
Laptop, Acer Extensa 5635ZG
Intel Pentium Dual Core 2x2,3 Ghz
2GB RAM
Nvidia Geforce G105M 512mb Vram

1. Problems with Wifi
Well, I've connected to my access point and everything works. But if I shut down my laptop or lose connection because of the distance, I'm not able to reconnect again. First, Kubuntu does not reconnect automatically, as set in the settings. Second, if i click on my connection, nothing happens. Also not after a hour.
The solution is to clear everything from the config and reboot the whole system, everytime.


2. Problems with delivered graphics driver and offical graphics driver.
The are graphics errors with the delivered graphics driver. Sometimes area rendering fails, that means "colorful pixel wars" on white background. Mostely this issue happens on windows (not THE windows :) ).
And with the official nvidia-current-driver, the screen is freezing after e.g. 30 minutes. Everytime and also in idle mode.

3.
Beamer configuration. If I want to do a presentation and I want to press the second-screen-button on my keyboard, nothing appens, while on windows the screen is switched to the beamer without any issue. 

4. VPN
I need to use a cisco-compatible VPN client for being able to go into the web from inside my university's network. So I've installed vpnc and it works well from the command prompt without any issue.
Under gnome there was a Gnome-Plugin for VPNC and it worked. Under KDE-Plugin (which I use now with Kubuntu) VPN does not work. I can connect to the VPN Server but if I click on the disconnect-icon, the whole KDE is freezing. Restarting X does not help. Rebooting does.

5.
Printer. Today I've bought a Canon Pixma IP3600 and nothing works. Plugged in the printer, but the installation did not start, as it did for printers at least under Ubuntu. Switched to K-Settings, installed the printer by clicking the button new printer. It was detected very well, but if I really want to print, simply nothing happens. A test page is not printed, too.
Ok, removed the printer and downloaded the driver from canon. There were several .deb files and I tried to find the root package, where all dependencies are installed. The dependencies of the root package were ok, but at the end it of the root .deb-package installation it said, that a library of cups is missing (fresh Kubuntu and updated installation). Tried to find it via package manager, it does not exist. Now i'm really fed up.

---

### Post by johanbove on 2011-07-01
> **Spitfire777 said:**
> Hi,

But very often I've got problems in the daily routine, where "normal" things do have to work, but they don't. Of course, Ubuntu is able to do more than Windows, but my opinion is that a modern OS does have to solve "normal" issues without using Google everytime and switching to the command prompt, customize config files in many cases for solving the problem. Well, after a fresh installation everything works yet, but if it comes to hardware support, special applications, etc. Ubuntu fails in many cases, what I can reproduce on various systems I have. My opionion is, that Ubuntu developers should work more on hardware support and reliability than working on **** (yes, S-H-I-T!) like Unity or other newer or "cooler" UIs.


Hello Spitfire777,

I feel your pain man. I'm currently having similar issues on my setup, my Vaio's CPU seems to run extremely hot and the fan speed control is bonked up, plus my Canon Pixma IP3600 refuses to work in 11.04 while it worked fine in 10.10. I also believe that Canonical should put their best effort on providing - perfect - hardware support for consumer electronics.

Heck, I would even pay for such a service if it meant that I could just go buy any device or laptop and it would work instantly with Ubuntu. I'm sooo jealous of Macintosh's support in that sense.

I know Canonical is far from Apple, but yet I see them as the only valid alternative alongside Apple and Microsoft, yet they seem to loose themselves in making the OS "look good" instead of offering basic functionality. But this is just my own opinion out of my current experience.

The truth is that if you choose to go Linux you are choosing the "DIY" - way, and hence, being in the Linux world will always force you to try to figure out how to solve problems on your own through Google searches and going through gazillion blogs from other Linux users. And to be honest, I like it, despite of all frustrations.

The result of all this that I'll make decisions on my next purchases based upon the support hardware builders offer towards Linux. Which means for me: NO MORE Sony and NO MORE Canon for me, instead i'm betting on HP/Lenovo and HP/Epson.

So hope you take care and best of luck.

---

### Post by coldraven on 2011-07-01
I started using Linux with Kubuntu 7 something (KDE 3.5). When KDE 4 arrived it was so broken I moved to Ubuntu. Some releases have been better than others, 10.10 works great for my HP laptop. I play around with 11.04 but will wait until 12.04 before I contemplate switching completely.
I booted the Live Kubuntu 11.04 recently but quickly realised that I still don't like it.

The best thing about Ubuntu is the massive help available through Google and this forum.
The next best thing is the ease of installing it.

Good luck, I'm sure you will resolve your problems one way or another.

---

