---
title: "Mouse Touchpad Not Edge Scrolling"
date: 2012-10-06
forum: General Help
---

### Post by CrusaderAD on 2012-10-06
Hello everyone. My left click wasn't working on my touchpad so I looked around and found this command:

```
sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

Which enabled it on reboot. Now edge scrolling doesn't work. Any ideas? I'm running Ubuntu 12.04 64bit on a Acer Aspire S3.

---

### Post by CrusaderAD on 2012-10-06
Also I did check and there isn't a setting pretaining to this in Mouse and Touchpad settings.

---

### Post by CrusaderAD on 2012-10-09
Bump

---

### Post by pqwoerituytrueiwoq on 2012-10-09
not sure if unity has the same mouse/touthpad gui as xfce but it is there is xfce
see screenshot

---

### Post by newb85 on 2012-10-09
I can confirm that that those scrolling options are standard in Ubuntu, as well.

---

### Post by CrusaderAD on 2012-10-10
```
sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

must have disabled those options as they're no longer in that windowed gui.

---

### Post by cortman on 2012-10-10
Have you tried running

```
synclient VertEdgeScroll=1
```

---

### Post by CrusaderAD on 2012-10-11
> **cortman said:**
> Have you tried running

```
synclient VertEdgeScroll=1
```

Didn't work, I got this error message:

> Couldn't find synaptics properties. No synaptics driver loaded?

---

### Post by cortman on 2012-10-11
Either your touchpad is an Elantech model or you don't have the proper driver loaded for Synaptics- running

```
xinput
```

would tell you which one you have.

---

### Post by CrusaderAD on 2012-10-12
Thanks. This is the output...

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; 1.3M HD WebCam                          	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=12	[slave  keyboard (3)]

```

---

