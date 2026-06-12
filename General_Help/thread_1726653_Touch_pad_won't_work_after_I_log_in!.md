---
title: "Touch pad won't work after I log in!"
date: 2011-04-11
forum: General Help
---

### Post by Dangerzone812 on 2011-04-11
Hey everyone,

I just put a fresh install of Ubuntu 10.10 on my HP Pavilion dv9000, and everything seems to be running well except for my touchpad! When I boot up into Ubuntu, the mouse works at the log in screen, but the second I sign in, it stops.

A USB powered mouse works, but not the touchpad. I even booted up from a live USB to make sure that it's not a hardware problem, and it worked there. Is there any way I can fix this easily? I don't want to have to do a fresh install, because I put all of my files back on it again as well as installed a bunch of applications and programs. 

Thanks in advance,

Danger.

---

### Post by matt_symes on 2011-04-11
Hi

Open a terminal and type

```
xinput --list
```

Post results back here.

Kind regards

---

### Post by Dangerzone812 on 2011-04-11
Output:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=14	[slave  keyboard (3)]

---

### Post by matt_symes on 2011-04-11
Hi

Your touchpad is recognised and that is good. Let's make sure it's not disabled in Gnome.

Open a terminal and copy and paste ...

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

Kind regards

---

### Post by Dangerzone812 on 2011-04-11
Holy Hector, IT WORKS! Thanks SO much!

Will I have to do this every time? Or is this gonna work from now on?

---

### Post by matt_symes on 2011-04-11
Hi

> **Dangerzone812 said:**
> Holy Hector, IT WORKS! Thanks SO much!

Will I have to do this every time? Or is this gonna work from now on?

1. No.
2. Yes  

Take care :D

Please mark this thread as solved.

Kind regards

---

