---
title: "Ubuntu/Firefox Lockup, it's recent, persistent and annoying."
date: 2010-08-02
forum: General Help
---

### Post by Sneux on 2010-08-02
Alright first some back story, a few months ago I switched from Windows XP to Ubuntu, best move I've ever made with my PC, everyday it was the infamous Ctrl+Alt+Del open task manager shut this or that off. After I switched to Ubuntu, it was like heaven, no crashing, no freezing, insanly fast load times.... Here is when it all changed.  A few weeks ago due to unrelated reasons I had to reinstall Ubuntu 9.10 onto my PC and did it with no problems, however, something has changed, after letting it update for a while I opened FireFox, installed my Add-Ons like Adblock Plus and NoScript and I like to watch my TV shows online such as old shows which I never had the time to watch or finish watching. All went very smoothly for a while then recently when using Firefox everything all of a sudden slows to a stop and locks up, I can move the cursor...that is all...none of the browser buttons will highlight when I put the cursor over them basically nothing responds to my input devices, mouse and keyboard, can't bring up terminal to shutdown the PC or Firefox I have to manually hold the button.  At first I thought it was a one deal thing...then it started happening more and more to the point where it happens 3-5 times a night and I have to completely shutdown and reboot, there are even times when the PC wont boot to the login screen.  I did a bit of investigating a found a lot of others who seem to have the same problem with Firefox 3.6 and up I am using Firefox 3.6.8 Starting today all my streaming shows lag horridly and if I try to open any other program while Firefox is running it locks up and I have to reboot.  (Not sure if it is relevant or not but I noticed a lot of people having issues with Plugin-Container for Firefox, I looked into it and found that that process is using more CPU Percentage than FireFox itself at around 40% when my videos are streaming, that is the second largest amount of usage, second only to the Xorg process which is working at times at 50%.  Any ideas? Should I upgrade to 10.04? Should I reinstall an older version of FireFox?  I have a feeling it is related to Flash but I wont claim to be positive on that speculation.

---

### Post by lovinglinux on 2010-08-02
It is flash, not Firefox.

Check the CPU temperature. Looks like it is getting too hot due to excessive CPU activity of the flash plugin.

Also see [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

---

