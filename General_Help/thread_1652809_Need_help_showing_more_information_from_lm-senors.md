---
title: "Need help showing more information from lm-senors"
date: 2010-12-25
forum: General Help
---

### Post by shattered.likeness on 2010-12-25
[SIZE=2]I have followed the guide [here]("http://ubuntuforums.org/showthread.php?t=2780") on the forums, and still can't get much to show up when running "sensors" from within terminal.

This is all that will show up when I run 'sensors' in terminal:
[/SIZE]> k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +6.0°C  (high = +70.0°C)                  



Here is my hardware specs:

> 
Processor:  AMD Phenom II X6 1090T
Motherboard:  MSI 790FX-GD70
Memory:  8GB Corsair XMS3 DDR3 1600
Video:  Sapphire HD 4850X2 2GB
Power Supply:  SilverStone ZM1200M
Case:  Silverstone FT01
hard Drives:  2x Kingston SSD  + 2x WD 1TB + WD 640GB


This has me puzzled, as I followed the guide exactly as it was stated, and I can't get everything working.  Is my hardware too new or something?

Thanks for any help you an give me.

---

### Post by ridgeland on 2010-12-26
I use sensors and use an applet in the panel to see temps.  Each new release I do a fresh install and take notes.  Here are my notes about sensors from when I installed 10.10

> SENSORS:
$ sensors - shows one! 
$ sudo sensors-detect 
	scan ISA/IO ports default NO - I said yes (still none found)
	add lines to /etc/modules default NO - I said yes
Reboot
$ sensors  --- should now show all fans and some temps.
synaptics - install sensors-applet --- option hddtemp deamon on boot - Yes
panel - add - hardware sensors, has value only
raise the second panel to about 34 pixels so there are two rows.
Settings for panel's hardware sensors:
First resize the windows to see the checkbox (long hard drive name needs it)
Move hddtemp down to bottom.
Turn on Fan1 and Fan2 - Click on the name wait one second and click on the name again to change the name  Fan1->CPU Fan2->Case
[Properties] Fan ranges CPU 800-3200, Case 600-2000
On both [x] enable alarm. - 20 seconds
Warnings low   	mplayer /usr/share/sounds/KDE-Im-Irc-Event.ogg 
Warnings high 	mplayer /usr/share/sounds/KDE-Im-Sms.ogg
Not certain if the three temp are three cores or one motherboard and two CPU. ?
I set temp 15-65 AMD and hard drives at 15-60
Same alarm and sound as for the fans.
In General Options choose "values only", hover for the names.
Changed panel height to 34 pixel and get the sensors in two rows, less space.

Maybe you'll see something useful.

---

### Post by shattered.likeness on 2011-01-02
Thanks for the info, but for some reason, I'm thinking that my hardware is not supported.  

Been trying to find a solution for the past several days, but still no luck.

---

### Post by dcstar on 2011-01-04
> **shattered.likeness said:**
> Thanks for the info, but for some reason, I'm thinking that my hardware is not supported.  

Been trying to find a solution for the past several days, but still no luck.

Go to the lm-sensors site and download and install the latest version:

[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

---

