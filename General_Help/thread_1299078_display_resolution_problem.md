---
title: "display resolution problem"
date: 2009-10-23
forum: General Help
---

### Post by delogren on 2009-10-23
Howdy,

Several months ago I got a Dell laptop with Ubuntu pre-installed. I fell in love.. So when the desktop died, I set up a dual boot system hoping to spend most of my time in Ubuntu. But no..

The problem for today is setting the display resolution. When I look in System->Preferences->Display on the desktop, the highest resolution is 800x600. On the laptop, there are numerous options.

After countless internet searches I was about to dive into editing xorg.conf. But when I looked at that file on the laptop, it was identical to the one on the desktop!

What am I missing here?

The monitor is a Samsung Syncmaster 2232bw and the video "board" is a nVidia nForce 620i..

tnx,
--del

---

### Post by john_navarro on 2009-10-30
This is what I have to do to get things to work for me. Keep in mind you have to run these commands every time you restart the machine. I have the same screen but am using it with a laptop docking station. This isn't a permanent fix but it will get you high resolution until something more permanent finds its way into the repositories.

xrandr "1680x1050_60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

xrandr --verbose --output LVDS1 --mode 1280x800 --output VGA1 --mode 1680x1050_60

My guess is that you might have to do:

xrandr "1680x1050_60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

xrandr --verbose --output LVDS1 --mode 1680x1050_60


Hope this works for you.
John

---

