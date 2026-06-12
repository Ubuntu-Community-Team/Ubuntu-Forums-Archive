---
title: "How to lower resolution from terminal"
date: 2012-04-30
forum: General Help
---

### Post by Silvertongue00 on 2012-04-30
First of all, I want to say sorry if I ask something trivial. This is my first time installing linux. I've dealt with blank screen after installation but I face another problem here.

After installation, I installed latest driver. After reboot, my PC autoconfigure resolution than my monitor capable. I want to reconfigure resolution from terminal. This is what i've done:

[LIST=1][*]go to terminal from login screen using ctrl+alt+F1 in login screen (when I do it, my monitor show "Input not supported")
[*]login using username and password
[*]xrandr -s (not working, it show "Can not open display")
[*]kernel /vmlinuz-linux root=/dev/sda1 ro vga=ask (not working as well, it show "kernel command not recognized")
[*]sudo gedit /etc/X11/xorg.conf (not working, it show wrong command for gedit)[/LIST]

then I googling again, I think I need to install ubuntu kernel sources, then I use sudo apt-get install linux-source. only this command works.

This is my source:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/using-a-terminal-to-change-resolution-672211/](http://www.linuxquestions.org/questions/linux-newbie-8/using-a-terminal-to-change-resolution-672211/)
[http://ubuntuforums.org/showthread.php?t=884157](http://ubuntuforums.org/showthread.php?t=884157)
[https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution](https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution)
[http://www.linuxtech.net/tips+tricks/Linux_Tips_and_Tricks_Collection.htmlhttp://forums.fedoraforum.org/archive/index.php/t-78268.html](http://www.linuxtech.net/tips+tricks/Linux_Tips_and_Tricks_Collection.htmlhttp://forums.fedoraforum.org/archive/index.php/t-78268.html)
[http://ubuntuforums.org/showthread.php?t=884157](http://ubuntuforums.org/showthread.php?t=884157)

---

### Post by dozdozez on 2012-04-30
emm..... 
well, i'm not sure to know what you are trying to do, but if your problem is that gedit is a wrong command, you can just install it using software center or synaptic.
If you prefer do so from command line, type: 
sudo apt-get install gedit

or you can use any oter text editor you like.

---

### Post by uylug on 2012-04-30
Okay, if you're doing a CTRL + ALT + F1, you're running in FULL CONSOLE MODE. Therefore no "DISPLAY" is available, therefore gedit won't work, and neither will xrandr.

xrandr is a tool to change the current resolution. Once the system restarts, the resolution reverts to what it's actually set. Xrandr doesn't save any settings.

**What you can do:**

```
export DISPLAY=:0.0
xrandr -s <your resolution here>
```

The export line will adjust the DISPLAY for you, and then run xrandr.

If you want to edit files without a DISPLAY, you could always use nano:
```

sudo nano /etc/X11/xorg.conf 
```

---

### Post by Silvertongue00 on 2012-04-30
> **dozdozez said:**
> emm..... 
well, i'm not sure to know what you are trying to do, but if your problem is that gedit is a wrong command, you can just install it using software center or synaptic.
If you prefer do so from command line, type: 
sudo apt-get install gedit

or you can use any oter text editor you like.

I'm so sorry if I use wrong command. This is the very first time using linux, and all I do is googling and trial and error. Thanks for advice, this is new knowledge for me :)

> **uylug said:**
> Okay, if you're doing a CTRL + ALT + F1, you're running in FULL CONSOLE MODE. Therefore no "DISPLAY" is available, therefore gedit won't work, and neither will xrandr.

xrandr is a tool to change the current resolution. Once the system restarts, the resolution reverts to what it's actually set. Xrandr doesn't save any settings.

**What you can do:**

```
export DISPLAY=:0.0
xrandr -s <your resolution here>
```The export line will adjust the DISPLAY for you, and then run xrandr.

If you want to edit files without a DISPLAY, you could always use nano:
```

sudo nano /etc/X11/xorg.conf 
```

yup, I want to lower my resolution from terminal. 
export DISPLAY=:0.0 command running well, but when I use xrandr -s 1024x768 or xrandr -s 1366x768 it got error message like this:

```

```

I've tried to change xorg.conf, but the content so different from this one [http://ubuntuforums.org/showthread.php?t=1947733](http://ubuntuforums.org/showthread.php?t=1947733)

while this one have complete section like this
```
Section "Device"
        Identifier "ATI Radeon"
        Driver "ati"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection

Section "Monitor"
Identifier	"Configured Monitor"
Vendorname	"Samsung"
Modelname	"Samsung SyncMaster 793S/793V/CM173G"
Horizsync	30-71
Vertrefresh	50-160
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
Gamma	1.0
EndSection

Section "Screen"
Identifier	"Default Screen"
Monitor	 "Configured Monitor"
Device	 "ATI Radeon"
Defaultdepth	24
SubSection "Display"
Depth	24
Modes	 "1024x768@70"	"1024x768@60"	"1024x768@75"	"1024x768@43"	"1024x768@85"	"1152x864@75"	"832x624@75"	"1280x960@60"	"800x600@60" "1280x1024@60"	"800x600@85"	"1400x1050@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72" "640x480@60"
EndSubSection
EndSection
```

in my pc don't have device and monitor section.

---

### Post by dozdozez on 2012-05-01
Have you tried that command ? :
sudo dpkg-reconfigure xserver-xorg

Aso, if you can't read your screen in graphics mode,  you should be able to lower the resolution in graphics mode just pressing ctrl+alt+(minus in keypad), or plus in keypad to move to a higer resoution.

I hope you find this helpful.

---

### Post by bodhi.zazen on 2012-05-01
You run xrandr in a terminal, from withing your graphical (X) session.

If you would like a graphical tool, install lxrandr.

[http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/](http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/)

If that does not work, what video card is it ? Some graphics driers, such as nvidia, have  their own tool.

---

### Post by Silvertongue00 on 2012-05-03
thanks so much uylug, that's work on me :D
I don't know how to repay it, but you're really help me

---

