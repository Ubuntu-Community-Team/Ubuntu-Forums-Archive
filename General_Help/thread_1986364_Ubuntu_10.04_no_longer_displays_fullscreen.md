---
title: "Ubuntu 10.04 no longer displays fullscreen"
date: 2012-05-24
forum: General Help
---

### Post by reefis on 2012-05-24
i've always had 1900x1200 but today i turned on my computer and it was changed to 1360x768 and there's no option for any higher resolution. wtf!? I really don't know where to start with this issue, google is not finding much. would this be an issue with my dell dimension 3000?
   the fan seemed extra loud yesterday, which usually happen when it's hot which it was. displaying flash videos full screen makes it sound the loudest as my computer can barely handle it... i'm hoping it's not my desktop... but today the fan seems extra quiet.
 can someone point me into the right direction?

---

### Post by reefis on 2012-05-24
this is my xorg.conf.failsafe.   i don't know why it says failsafe and there's no regurlar xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by reefis on 2012-05-24
so i googled xorg.conf.failsafe and  then found a post where someone suggested do this:
[code]
sudo cp xorg.conf.failsafe xorg.conf
sudo reboot now
[code]

now it won't even display. i used a LiveCD and noticed that it still doesn't display 1900x1200 even using the livecd, which it always did. what does this mean.... and also how do i fix this new problem i create with the failsafe?

---

### Post by reefis on 2012-05-24
So. How do I delete the xorg.conf file I created and is now causing my computer to not display at all.  How do I gain permission to do this using a livecd?

---

### Post by reefis on 2012-05-24
OK. i figured out the  xorg issue and 10.04 boots up and displays the way it did before i ****** it up more... so i'm back to this small resolution. WHY DID IT HAPPEN? anyone who can suggest a better forum to ask or website to go to i would personally love u deeply. i hate the fact i just wasted my night fixing this bull caccka

---

### Post by reefis on 2012-05-24
i'm a ******* genius. here's what i had to do, just in case this happens to anyone else
my monitor was undetected and never used a xorg.conf
**Adding undetected resolutions**

 Due  to buggy hardware or drivers, your monitor's correct resolutions may  not always be detected.  For example, the EDID data block queried from  your monitor may be incorrect. 
If the mode already exists, but just isn't associated for the particular output, you can add it like this: 

  $ xrandr --addmode S-video 800x600If the mode doesn't yet exist, you'll need to **create it first** by specifying a modeline: 

  $ xrandr --newmode <Mode``Line>You may create a modeline using the gtf or cvt  utility. For example, if you want to add a mode with resolution 800x600  at 60 Hz, you can enter the following command: (The output is shown  following.) 

  $ cvt 800 600 60   # 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz   Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsyncThen copy the information after the word "Modeline" into the xrandr command: 

  $ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsyncAfter the mode is entered, it needs to be added to the output using the --addmode command as explained above.

---

### Post by reefis on 2012-05-24
for some reason ubuntu always listed the name of my gateway monitor, under System>Preferences>Monitors.   for some reason it now reads my monitor as "unknown", which is baffling. so it seems to be an issue with ubuntu recognizing my monitor

---

