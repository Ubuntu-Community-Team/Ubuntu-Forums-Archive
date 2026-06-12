---
title: "Save external monitor settings"
date: 2010-09-22
forum: General Help
---

### Post by oscargodson on 2010-09-22
I have an external monitor at work, but not at home. I take my laptop home and when I come back the settings are off. My monitor is above my laptop, so I have to rearrage displays and save every time its plugged in. Isn't there a system file or something somewhere that I can write to and save the current state as the default?

---

### Post by efflandt on 2010-09-22
To use an external display with my laptop, I simply created a bash script with the **xrandr** commands to set the proper resolution, shut off my laptop display, and switch to the external display.  Then I make a launcher either in the top panel or on the desktop to run the script when I click on the launcher in top panel, or double click on the desktop launcher.

Note that if you create a **bin** directory in your home directory, the next time you login, ~/bin is automatically included in your path.  So you can run personal scripts there (as long as you gave them execute permission) by just the script name without needing a full path.

The names for your laptop display may vary depending upon your system and video chip.  Note that I have only done this for various default video drivers, so not sure how well it works with proprietary video drivers.  This is one example I used for 1080p, I think for Intel chip:

#!/bin/bash
# Add modeline
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
# Switch off laptop display
xrandr --output LVDS1 --off
# Activate HDTV on VGA
xrandr --output VGA1 --mode 1920x1080_60.00
exit

The **xrandr** command by itself can tell you what X calls your video outputs.

---

### Post by SaintDanBert on 2010-09-22
Where did you get the strings "VGA1" and "LVDS1"?

The sample script sets a specific mode for the external monitor.
If multiple modes are available, can I still use System --> Preferences --> Display to select among them once I wake the display?  Do I need to configure
other available modes somewhere?

~~~ 0;-Dan

---

### Post by oscargodson on 2010-09-23
> To use an external display with my laptop, I simply created a bash script with the xrandr commands to set the proper resolution, shut off my laptop display, and switch to the external display. Then I make a launcher either in the top panel or on the desktop to run the script when I click on the launcher in top panel, or double click on the desktop launcher.

Note that if you create a bin directory in your home directory, the next time you login, ~/bin is automatically included in your path. So you can run personal scripts there (as long as you gave them execute permission) by just the script name without needing a full path.

The names for your laptop display may vary depending upon your system and video chip. Note that I have only done this for various default video drivers, so not sure how well it works with proprietary video drivers. This is one example I used for 1080p, I think for Intel chip:

#!/bin/bash
# Add modeline
xrandr --newmode "1920x1080_60.00" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
# Switch off laptop display
xrandr --output LVDS1 --off
# Activate HDTV on VGA
xrandr --output VGA1 --mode 1920x1080_60.00
exit

The xrandr command by itself can tell you what X calls your video outputs.

Is there a way to find out the current settings though? For example, how do I make sure when I plug it in that the external monitor is centered above the laptop monitor as I'd see in the System > Preferences > Displays?

---

### Post by SaintDanBert on 2010-09-23
To follow-up to **oscargodson** comments, There are a lot of postings about X11 and Xorg. From where I sit, they mostly speak to an older way to do things. Said another way, they do not speak to the current set of X11 and Xorg features and tools.

Someone surely knows what is going on.  Someone can tell us.  Oddly, there is an abundance of silence.

Waiting,
~~~ 0;-Dan

---

### Post by booboo64 on 2010-12-31
In my situation I sometimes want to connect my netbook to an external CRT TV with a VGA input. To achieve this without having to manually specify the settings each time I've mapped this command to a keyboard shortcut.
xrandr --output VGA1 --right-of LVDS1 --mode 640x480

The general gist is that you're telling the VGA1 output to go to the right of the built-in (LVDS1) display and set it a specific resolution. Not entirely sure what all the other numbers relating to the resolutions are for in the previous posts, but they weren't necessary for me.

Whilst researching this I noticed that you can switch off displays (using "xrandr --output <output> --off") which you might find useful. The man pages have a wealth of information, but if you just want to do simple stuff (which is what I wanted to do) then you can just give it a go and see what happens.

To determine your output names you can use xrandr to see the name's assigned to them.

At a guess you'll need to use:
xrandr --output VGA1 --above LVDS1 --mode 1024x768 --primary --output LVDS1 --off
This will put your VGA output above the laptop, with a resolution of 1024x768 and make it the primary output, finally it'll switch off your laptop screen.

HTH, Bob

---

