---
title: "GPU fans always @ 0 RPM"
date: 2010-01-30
forum: General Help
---

### Post by phoenixfire82 on 2010-01-30
Just partitioned and installed Ubuntu 9.10. Everything up and running great, thanks for such an incredible (and free!) OS; just one little problem, all my fans are off except cpu fan and they don't come on regardless of how much stress is on the system. I had the same problem under winxp and vista but was able to use riva tuner and manually control the speeds of my 5 fans.

I'm mainly just concerned about my GPU fan(s?).  I Have an nvidia 9800 gx2 w/latest drivers and the fans stay at 0 rpm always (unless i manually change the speeds w/riva tuner under xp). Basically my problem is that I can't find a riva tuner equal. I have ls-sensors installed as well as gkrellm (which correctly monitors all my temps and fan speeds perfectly). I can get a readout in the gnome-terminal as well. Is there a program to control my fans under linux? If not, and anyone would be willing to post a walk-through to control them if that's possible, I'd greatly appreciate it. I fear for the health of my system which runs sometimes >65C @ idle.

I also looked in my BIOS but could find nothing indicative of fan controls.  Not sure what to try next :(

Here's what pwmconfig returned:
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is w83627dhg
   hwmon1/device is coretemp
   hwmon2/device is coretemp
   hwmon3/device is coretemp
   hwmon4/device is coretemp

Found the following PWM controls:
   hwmon0/device/pwm1
   hwmon0/device/pwm2
   hwmon0/device/pwm3
   hwmon0/device/pwm4
There are no usable PWM outputs.

___________________________________________________

Here's what >sensors returned:
-desktop:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.13 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +8.98 V  (min =  +5.91 V, max =  +4.22 V)   ALARM
AVCC:        +3.26 V  (min =  +0.00 V, max =  +2.40 V)   ALARM
3VCC:        +3.26 V  (min =  +3.33 V, max =  +2.08 V)   ALARM
in4:         +1.32 V  (min =  +1.55 V, max =  +0.01 V)   ALARM
in5:         +0.02 V  (min =  +0.66 V, max =  +0.00 V)   ALARM
in6:         +5.79 V  (min =  +0.51 V, max =  +3.89 V)   ALARM
VSB:         +3.26 V  (min =  +0.18 V, max =  +2.05 V)   ALARM
VBAT:        +3.17 V  (min =  +1.76 V, max =  +0.53 V)   ALARM
Case Fan:      0 RPM  (min =  224 RPM, div = 128)  ALARM
CPU Fan:    1757 RPM  (min =    0 RPM, div = 128)
Aux Fan:       0 RPM  (min =    0 RPM, div = 128)
fan4:          0 RPM  (min =    0 RPM, div = 128)
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +27.0°C  (high =  +6.0°C, hyst =  +8.0°C)  ALARM  sensor = diode
CPU Temp:    +16.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +40.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +2.500 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +39.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +39.0°C  (high = +76.0°C, crit = +100.0°C)  


Thanks in advance for any help.

---

### Post by imjafo on 2010-01-30
Phoenixfire: I use nvclock_gtk to set my fan speed. It is available thru synaptic. You need to d/l nvclock and nvclock_gtk. After down loading, enter sudo nvclock_gtk in the terminal, it will bring up nvclock and there is a setting to control fan speeds. As a side benefit, you can also overclock you card if you want to, as nvclock uses Coolbits. I made a launcher for the top panel by going to the top panel, click on add to panel, create a custom launcher, open you file system and go to usr/bin, find nvclock_gtk executable, right click on it and copy, paste into the command box for the application launcher, enter nvclock_gtk into the name box. Close the application box. You should now have a new launcher in your top panel. Click on it and nvclock should open, allowing you to adjust your fan speeds. This is a per session setting only, I don't know haow to make the settings stick, yet. Hope this helps you. If you have more questions, just ask.

---

### Post by phoenixfire82 on 2010-01-30
Thanks a million, I will definitely try this when I get home and report the result!

---

