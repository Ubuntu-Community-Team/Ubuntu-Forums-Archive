---
title: "External monitor not detected and flashes on and off standby with docking station"
date: 2012-05-18
forum: General Help
---

### Post by wolfsilentheart on 2012-05-18
Hey guys,

I'm fairly new with linux but I have some basics down. I have a Dell Latitude E6520 with Nvidia graphics running Ubuntu 12.04 64 and using the Unity desktop. 

I've been trying to get my laptop to work with a docking station for some time, I also had the same issue in the previous LTS version. When I use the docking station the external monitor is connected through DVI and flashes the "entering power save mode" message, enters standby, turns on, and repeats over and over. The monitor is known good. I removed the docking station from the equation and connected a VGA cable to my laptops external monitor port and nothing happens at all, I have also verified I selected the VGA input on the monitor. I used the display settings to try to detect the external display, both with and without the docking station and no external monitor was detected. I've also run xrandr and it does not seem to see anything other than my built in display, but I'm also not entirely sure if that is normal or not.

Any assistance will be greatly appreciated!

:confused:

---

### Post by wolfsilentheart on 2012-05-22
SOLVED:

Used nvidia-settings to enable the secondary display. The built in video settings application does not detect the display but nvidia's does.

---

