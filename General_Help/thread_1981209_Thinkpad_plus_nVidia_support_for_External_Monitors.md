---
title: "Thinkpad plus nVidia support for External Monitors"
date: 2012-05-16
forum: General Help
---

### Post by kettlehell on 2012-05-16
This post is a clarification and summary of an earlier post (here: [http://ubuntuforums.org/showthread.php?p=11936025#post11936025](http://ubuntuforums.org/showthread.php?p=11936025#post11936025)). My machine stats are at the bottom for reference.

Background:
I cannot seem to get anything working with external displays. I've discovered that the 2 graphics cards in the machine are set up as described here ([http://zachstechnotes.blogspot.com/2012/01/tri-head-display-on-linux-thinkpad-w520.html](http://zachstechnotes.blogspot.com/2012/01/tri-head-display-on-linux-thinkpad-w520.html)). The Intel Card is wired up to the Thinkpad display and the VGA, the nVidia card is wired up to all ports (only 2 can be used at any time). The zachtechnotes post (above) seemed to be the most promising for me; but nothing worked exactly as described, even though my machine is remarkable close to his. Currently, I've stuck to integrated graphics, and simply used Laptop display and VGA out.

Problem:
I would like to be able to set up to configurations. I don't mind a bit of setup and hacking to switch between configurations, nor do I care about battery life:

config 1) use the VGA output and the displayport output on the laptop to extend my desktop (TwinView). Laptop would be closed.

config 2) use laptop only (i.e travel)

config 3) use the laptop display and the display port output to extend or mirror.


Tries:
I) First attempt was the "out of the Box" method. Pop in an ubuntu ISO, connect up monitors, and try to extend using "Displays" and xrandr.

II) download and install "nvidia-current", change BIOS to Discrete, restart. Horrible resolution on restart (600 x 800 ish), unable to change resolution higher, no recognition of any monitors on "Displays" or xrandr. Tried using nvidia-settings.."You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

III) download and install bumblebee, change BIOS to "Optimus". restart. Tried using nvidia-settings -c :8, and the external monitor on display port is recognized, but no another displays are. TwinView option is disabled (likely because there is only one monitor). With this mode, I can issue a command like: "optirun gedit DISPLAY :8" and gedit pops up on the external monitor, but it is ugly, and there is no mouse movement.

IV) ... HELP !!

I'm tempted to try purging bumblebee, reinstalling nvidia drivers, deleting all the xorg.conf things I've monkeyed with and set BIOS mode to discrete. Then pray. Then restart and hope 'nvidia-settings' comes up without an error message.


Any thoughts? Please help.


--
os: Ubuntu 12.04 (precise)
Lenovo Thinkpad 420s
Processor: Intel Core i7-2640M Processor (2.80GHz, 4M Cache with Turbo Boost up to 3.50GHz)
Display type	 14.0" HD+ (1600 x 900) LED Backlit AntiGlare Display, Mobile Broadband Ready
System graphics: NVIDIA Quadro NVS4200M Optimus technology (1GB), Sandybridge Integrated Graphics
Total memory	 8 GB PC3-10600 DDR3 SDRAM 1333MHz SODIMM Memory (2 DIMM)
Hard drive	 500GB Hard Disk Drive, 5400rpm

---

### Post by sunbergzach on 2012-05-16
I think that in your case, the quickest way to get everything working is to

1) purge bumblebee (bumblebee and discrete bios seem to be mostly incompatible)

2) download and install the latest nvidia drivers from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) (this is kind of a brute force install method - your package manager probably won't know that you have nvidia installed - but it seems like it works more reliably than trying to install the nvidia driver using ubuntu's utilities).

3) run in discreet mode and use disper and nvidia-settings to switch between configurations (xrandr won't work)

The only downside to this is that the nvidia card will always be running, so you will have worse battery life (about 30% worse in my experience with the W520).

Long term, you can run in optimus mode with the display port using a utility called screenclone
([https://github.com/liskin/hybrid-screenclone](https://github.com/liskin/hybrid-screenclone), [http://zachstechnotes.blogspot.com/2012/04/post-title.html](http://zachstechnotes.blogspot.com/2012/04/post-title.html)), but this will take some hacking.

---

### Post by kettlehell on 2012-05-16
sunbergzach, I appreciate your feedback.

Any special ideas on getting the nvidia-settings to recognize the fact that I'm using the nvidia driver and preventing,... "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." message.

Also, I've had some issues with 3d ubuntu unity working with Discrete. Could that also be because bumblebee was interfering..

Going to try it today around 5 ET. I'll let you know what happens.

Thanks again.

---

### Post by kettlehell on 2012-05-16
Also, I've had some issues with 3d ubuntu unity working with Discrete. Could that also be because bumblebee was interfering.

---

### Post by kettlehell on 2012-05-17
Solved.

1) purge bumblebee

2) download latest nvidia driver from web. (no from ubuntu package manage)

2) exit the X server

3) install nvidia (follow instructions carefully, allow it to disable nouveau)

4) set BIOS mode to Discrete

5) restart.

---

