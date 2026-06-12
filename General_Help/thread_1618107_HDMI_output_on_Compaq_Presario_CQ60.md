---
title: "HDMI output on Compaq Presario CQ60"
date: 2010-11-10
forum: General Help
---

### Post by reklame on 2010-11-10
Hello.

I'm new in this, but i'm rellay starting to enjoy linux. 

But, i have one huge problem, that is really important for me.

When i plug a HDMI cable in my computer, it doesnt show any pictures on my TV. In nVidia controlpanel it shows in Xserver Display configuration. I tryed to check the "TwinView" box, but it still doesnt work.

Here's som info that i learned was important to get help:

```
lspci | grep -i vga
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)

``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any sugestions how to make it work?

---

### Post by ngrieb on 2010-11-10
Did you hit the "apply" button after checking the "twin view" setting? I know it is a dumb question, but lets start simple. Also are you sure that the TV is on the right input setting, etc.?

---

### Post by reklame on 2010-11-10
> **ngrieb said:**
> Did you hit the "apply" button after checking the "twin view" setting? I know it is a dumb question, but lets start simple. Also are you sure that the TV is on the right input setting, etc.?

yes and yes

---

### Post by reklame on 2010-11-10
> **reklame said:**
> yes and yes

Now here's a update. I got picture on my TV. I changed the videocard driver to another... (it said not recomended)..

**NOW theres no picture when i play movies on my PC, and theres no sound on my TV..** :-s

---

### Post by ____ on 2011-03-27
I have the same video card as well and am having similar problems. Although I can not get it to display anything.

---

