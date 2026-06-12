---
title: "Crashing on all environments..."
date: 2009-10-05
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2009-10-05
I've tried every OS and every driver combination and I just can't seem to keep anything running. After so long of being on the computer just crashes. In ubuntu and other linux distros I've been seeing the screen go to rainbow colors and have to hard reset... in windows it's a blue screen of death. I've tried Ubuntu 8.04, 8.10, 9.04 and Windows XP Pro x64, Vista Ultimate x86, and 7 build 7100 and all do the same thing. See signature for hardware details. I can't think of anything else I can do... Don't know how I can find out what is causing the problem nor if the problem is fixable. I have warranties on all the hardware but would rather not have to deal with that. Anyone out there have something for me?

Oh and to add to the signature... I just added a wintv 1800 tuner card, a 500 GB hard drive SATA, and a 40 GB hard drive IDE. All drives got fscked with no errors and the system runs awesomely otherwise. I was thinking overheating somewhere??

---

### Post by pmains on 2009-10-05
So, you've established that the OS isn't the problem. It must be hardware. Specifically, the motherboard is your best bet (especially if everything is new enough to still be under warranty). I can also see defective RAM as a possibility.

---

### Post by Sin@Sin-Sacrifice on 2009-10-05
Yeah.. I took that into consideration but I've noticed people with similar problems with the nvidia drivers and was hoping that might be one of the issues. Shouldn't have that problem in windows though... guess if there's no other steps that can be taken I will go to XFX for a new board. Oh bother...

---

### Post by gali98 on 2009-10-05
You might see if your motherboard has a diagnostic disk to go with it...
Kory

---

### Post by Sin@Sin-Sacrifice on 2009-10-06
Hey thanks... The only disk was a driver disk for windows. I think it does come down to ram. I used each one individually and come to find that it does it on one but not the other. Then again... they were pretty hot so I might just need to find a way to cool them better. By the by... could any of these alarms have anything to do with my issues?```
Killmandline:$ sensors
w83627ehf-isa-0a10
Adapter: ISA adapter
VCore:       +1.31 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.83 V  (min =  +8.87 V, max =  +9.87 V)   ALARM
AVCC:        +3.28 V  (min =  +3.38 V, max =  +1.89 V)   ALARM
3VCC:        +3.30 V  (min =  +0.94 V, max =  +0.24 V)   ALARM
in4:         +0.95 V  (min =  +0.98 V, max =  +0.46 V)   ALARM
in5:         +1.16 V  (min =  +1.69 V, max =  +1.42 V)   ALARM
in6:         +5.22 V  (min =  +3.25 V, max =  +6.20 V)   
VSB:         +3.30 V  (min =  +2.93 V, max =  +2.29 V)   ALARM
VBAT:        +3.06 V  (min =  +0.94 V, max =  +0.67 V)   ALARM
in9:         +1.30 V  (min =  +1.51 V, max =  +1.17 V)   ALARM
Case Fan:   3515 RPM  (min = 1328 RPM, div = 8)
CPU Fan:    3375 RPM  (min =  770 RPM, div = 8)
Aux Fan:    2109 RPM  (min =  697 RPM, div = 8)
fan4:          0 RPM  (min = 1506 RPM, div = 128)  ALARM
fan5:          0 RPM  (min =  703 RPM, div = 128)  ALARM
Sys Temp:    +21.0°C  (high = -17.0°C, hyst =  -8.0°C)  ALARM  sensor = thermistor
CPU Temp:    +40.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +49.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

```

---

### Post by ApEkV2 on 2009-10-06
Try taking out all your ram except one, (one module could be bad, and that could be causing it)

---

### Post by Sin@Sin-Sacrifice on 2009-10-06
That's what I just did... then I switched to the other. I have 2 corsair CM2048s... seems as though the one is working quite well as oppose to the other one crashing after 10 min. I've been on this one for about 3 hours now and all is well so far in Ubuntu 9.04. I noticed my voltages are a bit high from what I've read but mostly from old threads and blogs. I tried reading the schematics from AMD but got nowhere there because it's in Vulcan mixed with Goa'uld or something... Not savvy at all. Regardless I found some human readable "suggestions" from posts and whathaveyou and seems like I'm ok on the temps and voltages. (PLEASE TELL ME IF I'M WRONG!!!) If all goes well after testing the RAM some more then Corsair will be hearing from me... even though I can't use the 4GB in 32bit OSs. Thanks again everybody.

---

### Post by Sin@Sin-Sacrifice on 2009-10-06
Didn't even think about memtest... but confirmed... Thanks for the help and sorry about the duhhh...

---

### Post by Sin@Sin-Sacrifice on 2009-10-07
Ok... I did find a bad module but seems like when I encode video I still get the same kind of crash. Did memtest right after and everything is fine. Could it possibly be the nvidia chipset? Is there a way I can check hardware that's on-board?

Side note: Since I found the bad RAM I only see this when using devede on both windows and linux. That's where I get the idea of nvidia perhaps being the problem. Anything on the voltages? They are all set to auto in the BIOS and I don't know if I want to change them.

---

### Post by gali98 on 2009-10-12
It could be the nVidia... Are you on restricted drivers?
And I wouldn't mess with the voltages....
You might search google for the windows problem, as probably more people are using it with windows than linux.
You might experiment with other processor intensive apps to see if they also crash.
I suggest:
blender
glxgears (this is already installed. Just run that command from the terminal.)
quake live - quakelive.com (it's free, and it runs in the browser. If anything would make it crash, this would.)

Kory

---

### Post by CatKiller on 2009-10-12
It's worth taking the time to inspect the motherboard carefully. Look for any capacitors that have a domed top or are cracked or leaking.

---

### Post by Sin@Sin-Sacrifice on 2009-10-17
Thanks guys for all the help but, even though I got it working and quite well, I don't know what was causing the problems because I tested 2 or 3 things at a time. I do it that way because if I don't then I will forget 2 and 3 while testing 1... if that makes sense. Anyway... I now have both ram sticks in and passing memtest and there hasn't been a crash in 3 days. The issue went away both in windows and linux at the same time. The only changes I made were setting the BIOS to performance defaults and then tweaking the linkwidth from 8 to 16, changed DDR clock from 400MHz to 800MHz and then reset my CPU clock (only 2.4GHz from 2.2), and now, because of testing, the RAM is mounted in different slots. Nothing will crash this system now... I ran GTA 4 at the highest my system can handle and even though I only got about 8 FPS it never crashed and I could get to the settings to change it back to usable. I also tried the quake live and all went well. Still confused but certainly happy. Again... thanks for everything.

---

