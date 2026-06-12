---
title: "Weird Black Marks"
date: 2009-07-05
forum: General Help
---

### Post by Nikayah on 2009-07-05
I am running Ubuntu Jaunty 64 bit.

For some reason I have these weird black marks in the upper left hand corner of my screen. They usually stay on top of everything, the only thing I've found they they stay beneath are windows that are moving (I have wobbly windows active) and the cursor. I think they appeared when I started using the compiz effects. (Extra Visual Effects in the Appearance Preferences menu)

[http://img11.imageshack.us/img11/9628/screenshotsvw.png](http://img11.imageshack.us/img11/9628/screenshotsvw.png)

I was hoping someone would know how to fix said spots.

---

### Post by t4thfavor on 2009-07-06
info on graphics hardware, and config would probably help us narrow it down. Try posting some system specs, and see where you end up.

It does sound like a hardware issue to me, could be heat.

---

### Post by Nikayah on 2009-07-06
I have an NVida GeForce 8600 GT. As for my config I assume you mean the Compiz effects config. I'm just running the default Extra Visual Effects in the Appearance Preferences menu. If there's some utility to dump the config (or just a config file) I'd be glad to provide.

---

### Post by t4thfavor on 2009-07-06
install some temperature monitoring software like sensors-applet. Then see if you are getting any abnormally high temperatures.

Other than that it could be faulty hardware. I have nvidia cards, and have never experienced such an issue. I am afraid I am at the end of my expertise.

---

### Post by Nikayah on 2009-07-06
The Nvidia X Server Settings displays a temperature of about 58/59 C and here's the output from sensors.

```

it8716-isa-0e80
Adapter: ISA adapter
VCore:       +1.04 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:         +4.89 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +12.16 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:        +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:        +3.28 V
fan1:       3308 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =   10 RPM)  ALARM
temp1:       +52.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +28.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +25.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.550 V

```

I'm running an AMD Phenom 9500 (4 * 2.2GHz) I think the black marks might have something to do with the proprietary NVidia driver. I'm not sure though.

---

### Post by Nikayah on 2009-07-06
It seems that if I log out then back in after my initial login they dissapear. 
```

1)Boot
2)Login
3)Logout
4)Login
5)No More dot thingies

```

However, a more elegant solution would be appreciated if anyone knows of one.

EDIT: compiz.real --replace does not remove the dot/mark things

---

### Post by tgalati4 on 2009-07-06
I get a black square in the upper left corner running XFCE (32-bit) that I have noticed on several machines.  I thought it was bad video RAM, but since this happened on 3 different machines with different video hardware, I chalk it up to an XFCE/xorg bug.

You may be experiencing something similar.  I have run 32-bit without problems on an nVidia 8600, but I haven't installed 64-bit yet so I can't comment.

Try changing resolutions and refresh rates and make a table of what artifacts that you see in each combination.

---

### Post by Nikayah on 2009-07-07
I think that I fixed it... I attempted to install version 185 of the driver from the nvidia site, but failed. I then reinstalled the nvidia-glx-180 driver from the repos, and now I don't have the weird artifacts.. I think this is now solved, somehow..

---

