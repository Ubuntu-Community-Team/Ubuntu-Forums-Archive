---
title: "How do I disable 'X Server' so I can install Nvidia drivers?"
date: 2012-03-10
forum: General Help
---

### Post by JRDN850 on 2012-03-10
I am trying to install Nvidia graphics display drivers but it says I must disable X Server first.
 
I have read that I need to press CRTL+ALT+F(1-6) to get into a TYY terminal.
 
I am not able to login when it asks me to. It says "[hostname] login:" then I can my user name here... and then it says "password:" No matter what username/hostname/account name I use (I think I gave 2 very similar names during install) the password is not correct.
 
Is there some username password that I am supposed to setup for this? The username/password I use to log into the Desktop when I turn my computer on isn't working.
 
--------------Question #2----------------
 
Let's say I can log-in properly. How do I disable 'X Server' inside the TTY terminal? There is a specific code I can type in? Then what, do I just open the driver .run file as normal from inside this TTY terminal?
 
From inside this TTY terminal nothing changes compared to the regular terminal? I still get root by typing 'su' and giving password? I can still change directories to locate the driver .run file and open it all the same?
 
 
If you could help me in as much detail as possible, I'd appreciate it.

---

### Post by JC Cheloven on 2012-03-10
question 1.- you should provide your usermane (enter) and password (enter). If that doesn't work for you, you have a different, more serious problem, than the title of the thread (please start a new specific thread if the problem persists).

question 2.- to stop the xserver temporalily, type ```
sudo service gdm stop
```
when you're done installing nvidia drivers, you probably will want to reboot, which is done with ```
sudo shutdown -h now
``` (this will in fact turn off your pc, giving you the chance of a cold reboot, which imo can be more convenient than a simple reboot).

---

### Post by JRDN850 on 2012-03-11
I appreciate the direction (I found out I have lightdm, not gnome)
 
So now in trying to get graphics functionality I have an even bigger problem.
 
I installed the linux Nvidia driver that is compatiable for my GeForce 9800 GT card.
 
Right before the install, I get the error message "The distrobution provided pre install script failed, continue anyways?" I continued and it appeared to install the driver. After restart, the driver doesn't work, but at least now everything is 4:3 proportional on the screen (in a massive resoultion, of course), I can now see everything on the screen. (Before the whole far left of the screen was clipped off, so I couldn't access the Desktop menu or close windows that had been maximized.
 
So now I can at least explore was Ubuntu has to offer, and under the "system settings" window, I see there has been a check for additional drivers.
 
On this list of avalible additional drivers, is 4 Nvidia drivers. I belive all of them listed where the same driver, but some where updated versions or revised versions. I clicked the one that had "(recommended)" after the name and installed that.
 
Big problem. I get the error message: 
 
"None of the selected modes were compatible with the possible modes
Trying mode CRTC 351
Trying mode CRTC 351
Trying mode CRTC 351"
 
I can't even log in to the desktop, there is a glitch now in the X Server. When I boot up, it runs a giant services check list and under one particular item it says "failed" in red text.
 
I don't even know what it is, because this is in terminal and the first Nvidia driver I install was overwritten, so the entire picture isn't on my monitor and I can't see the left side of the screen where it's describing the name of what failed.

---

### Post by Paqman on 2012-03-11
Is there some reason you're trying to install your graphics drivers manually? By far the best and easiest way to install them is to open up Hardware Drivers and install the driver it offers.

---

