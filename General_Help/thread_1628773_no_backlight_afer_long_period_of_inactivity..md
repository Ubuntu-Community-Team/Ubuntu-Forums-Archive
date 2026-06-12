---
title: "no backlight afer long period of inactivity."
date: 2010-11-23
forum: General Help
---

### Post by vsespb on 2010-11-23
Hello.

Kubuntu 9.10/10.04
Desktop, ASUS P5QL/EPU Nvidia 9400 GT + LCD Philips 190x6 

In the morning I cannot use my desktop cause screen backlight is turned off.
I tried turn off screensavers (system settings/display) and power managment functions (system settings/power managment).

It's not helping

Computer runs screensaver. In the morning I cannot use it cause no backlight.
However if I run sleep and wake up in a 5 min everything is ok.

I've tried google for commands which turn/off set/get brightness of screen - no one working for me.

1. How to turn off display power management ?
2. or maybe there is a reliable way to fix this ?
3. or how do I reproduce the bug (i dont want to wait morning each time)
4. Found interesting thing "--quirk-reset-brightness" in /usr/lib/pm-utils/video-quirks ? How to test it ?

---

### Post by vsespb on 2010-11-24
even killing XServer does not help waking up.

also I am trying run

sudo -u vse xset dpms force on
sudo -u vse xrandr --output default --mode 1024x768
sudo -u vse xrandr --output default --mode 1280x1024

from /etc/pm/power.d/

it all failed with

unable to open display ""                                                                                                             
Can't open  Display                                                                                                                                                                  
Can't open display

---

### Post by vsespb on 2010-11-24
moved from KDE to GNOME and disabled ACPI in BIOS. this helped.

---

### Post by vsespb on 2010-11-25
aha it happened again!

---

### Post by morepractice on 2012-12-05
vsespb, could you please tell us how you got around this problem?

---

### Post by vsespb on 2012-12-05
> **morepractice said:**
> vsespb, could you please tell us how you got around this problem?
Yes :) That was not Ubuntu problem. Hardware problem (monitor PSU capacitors). Was 100% fixed when replaced capacitors.

p.s.
Sorry, I remember I found it only after couple of month after I wrote last message in this thread.

---

