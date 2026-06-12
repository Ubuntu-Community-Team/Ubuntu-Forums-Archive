---
title: "[lucid] can't adjust screen brightness using function keys"
date: 2010-05-03
forum: General Help
---

### Post by Lawand on 2010-05-03
I have just upgraded to xubuntu 10.04 and although some function keys are working (like volume control), the screen brightness function keys aren't (the screen brightness is at top level and can't be reduced)

Notes:
[LIST]
[*]I am using a Compaq 610 laptop
[*]The brightness keys are working on Ubuntu 10.04 (live session)
[/LIST]

How can I fix this?, and at least is there any other way to adjust screen brightness?

---

### Post by Lawand on 2010-05-04
Apologies for bumping, but this is really an annoying problem.

Any help is appreciated.

---

### Post by Lawand on 2010-05-04
Problem solved, I installed Gnome Power Manager and removed Xfce Power Manager.

Now I can adjust screen brightness using function keys :)

---

### Post by Linfreak on 2010-05-14
Hi I have the same problem. Am running Ubuntu 10.04 and I have gnome-power-manager installed. But though the brightness bar seems to show the change in the level when using the function key and <Right,Left> keys, the actual brightness still remains at the highest level. 

As you've stated this is really annoying when working at night.

I am willing to try anything to solve this.

Thanks in advance,
Siva

---

### Post by kmsalex on 2010-05-15
bump

I've got the same problem on Ubuntu 10.04, i can't adjust i either by the function keys or by the brightens applet. I can add it to the tool bar and when i click on it i get the drop down slider but when i click that the slider just disappears.

Any suggestions are appreciated.

---

### Post by otkaz on 2010-05-27
Same problem here using ubuntu 10.04 with gnome-power-manager installed on a HP elitebook 8530p. FN keys and desktop display applet will not adjust the display. when I first boot my display is pretty bright with either it plugged into ac or not until i either plug or unplug for the first time then the display dims some, but will not get bright again plugged or unplugged, also /proc/acpi/video/DGFX/LCD/brightness shows it set to 100% at all times it never changes. I'm using the ati driver tried running aticonfig --acpi-services off, but it made no difference. It worked fine in karmic and ibex...

---

### Post by kiaraz on 2010-07-04
> **otkaz said:**
> Same problem here using ubuntu 10.04 with gnome-power-manager installed on a HP elitebook 8530p. FN keys and desktop display applet will not adjust the display. when I first boot my display is pretty bright with either it plugged into ac or not until i either plug or unplug for the first time then the display dims some, but will not get bright again plugged or unplugged, also /proc/acpi/video/DGFX/LCD/brightness shows it set to 100% at all times it never changes. I'm using the ati driver tried running aticonfig --acpi-services off, but it made no difference. It worked fine in karmic and ibex...


I'm having the saaame problem! Did you find a solution??

---

### Post by markwend on 2010-07-23
Ditto for me on an HP Pavilion dv6000 laptop. Frustrating that it used to work in older versions of Ubuntu, but hasn't for a while now. The lcd brightness panel just closes when I click on it, and the brightness function keys are unresponsive.

Any way to mark this thread 'unsolved'?

---

### Post by Vaphell on 2010-07-23
simply start a new thread :)

---

### Post by zemoffm on 2010-08-11
I'm also having this issue, hp pavilion dm1z-2000 on 10.04.  Is there an official bug for this or at least a report with a workaround/solution?

---

### Post by yjlego on 2011-06-10
I tried on my Ubuntu 10.04 Lucid Lynx 64 bit, Thinkpad T510. Previously I cannot use the keyboard shortcut key to adjust the brightness. I have also tried 
sudo setpci -s 00:02.0 F4.B=xx
as suggested by many posts but without any luck. Fortunately, this problem is solved by the following method. 

1. In the terminal, type

sudo gedit /etc/X11/xorg.conf

2. In xorg.conf, add the following line in Section "Device"

Option          "RegistryDwords"    "EnableBrightnessControl=1"

3. Logout, and login again. 

Congratulations! Now you are able to adjust your screen brightness with your Fn key.

---

### Post by Frantic_Earthling on 2011-06-10
This worked on my Asus M70Vn.

Many thanks!

---

### Post by Otto-C on 2011-07-18
No /etc/X11/xorg.conf file in my Lucid 10.04.

otto-c

---

### Post by DarrenMR415 on 2011-07-18
> **Otto-C said:**
> No /etc/X11/xorg.conf file in my Lucid 10.04.

otto-c

Make sure the X in X11 is capitalized. 

[http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10](http://ubuntuguide.net/change-screen-brightness-with-fn-key-in-ubuntu-11-0410-10)

---

### Post by Otto-C on 2011-07-21
Lucid 10.04.

My solution was:

System > Preferences > Power Management
At Power Management Preferences click On Battery Power and
untick Reduce backlight brightness.
Authenticate w/password and your good to go.
otto-c

---

### Post by johny why on 2012-05-19
> **Otto-C said:**
> System > Preferences > Power Management

where is this on lucid 5.2.8?

thanks

---

### Post by ka823 on 2013-04-07
@yjlego: Thanks for the reminder, this works on 12.04 on a Thinpad 510.

..
1. In the terminal, type

sudo gedit /etc/X11/xorg.conf

2. In xorg.conf, add the following line in Section "Device"

Option          "RegistryDwords"    "EnableBrightnessControl=1"

3. Logout, and login again.
..

---

### Post by oldos2er on 2013-04-07
Old thread closed.

---

