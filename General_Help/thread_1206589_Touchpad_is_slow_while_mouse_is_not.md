---
title: "Touchpad is slow while mouse is not"
date: 2009-07-07
forum: General Help
---

### Post by MockY on 2009-07-07
I just bought a new laptop since the hinges fell apart on my beloved Gateway. I'm now a Vaio NW150J owner and everything works just fine (apart from the internal mic). However, what I did notice is that the responsiveness of the mouse pointer when using the touchpad is very slow compared to when I use a mouse. I can increase the sensitivity in mouse settings to an acceptable level, but that makes the mouse pointer super fast when using the mouse.

Is there a way to increase the sensitivity for the thouchpad only?

---

### Post by damis648 on 2009-07-07
Open a terminal and input:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
and after the line
```
<merge key="input.x11_driver" type="string">synaptics</merge>
```, put in the following:
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
<merge key="input.x11_options.MinSpeed" type="string">0.45</merge>
<merge key="input.x11_options.MaxSpeed" type="string">0.95</merge>
<merge key="input.x11_options.AccelFactor" type="string">0.06</merge>

```
and log out and back in to see changes. Go ahead and play with the values until you find something comfortable.

---

### Post by moster on 2009-07-07
I had that problem on previous version of Ubuntu. I solve it by installing Gsynaptic. It is some little app that let you fine tune touchpad. Go to add/remove and searc for "gsynaptic".

---

### Post by MockY on 2009-07-07
Thanks for your responses.

Gsynaptic only generates the following error:```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics 
```
I am going to try what is suggested in this post [http://ubuntuforums.org/showpost.php?p=3204614&postcount=9](http://ubuntuforums.org/showpost.php?p=3204614&postcount=9)

And following what damis648 suggested returned in no changes.

**Side Note:** I am using Intrepid Ibex on the laptop (Tama) since it has an Intel graphic card. The profile distro is based on my desktop computer (Mapex)

**EDIT:**
I could not follow the instructions in the post I mentioned because my xorg.conf file is almost empty. This is the only thing I have in that file:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by moster on 2009-07-07
Sorry for not giving you complete information. ok.. here.

enter first this in terminal to open that xorg as admin
```
gksu gedit /etc/X11/xorg.conf
```

then just add this at bottom and restart computer.

```
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"  "true"
    Option      "Device"          "/dev/psaux"
    Option      "Protocol"        "auto-dev"
    Option      "HorizEdgeScroll" "1"
    Option      "MinSpeed"        "0.60"
    Option      "MaxSpeed"        "1.10"
    Option      "AccelFactor"     "0.030"
    Option      "EdgeMotionMinSpeed" "200"
    Option      "EdgeMotionMaxSpeed" "200"
    Option      "UpDownScrolling" "1"
    Option      "SHMConfig"       "on"
EndSection
```

This is original page
[http://www.zyxware.com/articles/2008/05/22/is-your-touchpad-too-slow-in-ubuntu-fix-it]("http://www.zyxware.com/articles/2008/05/22/is-your-touchpad-too-slow-in-ubuntu-fix-it")

Now must work that gsynaptic. Just hold on till next ubuntu, your problems for which you are on 8.10 will be gone. They make that right as well as bunch of other stuff I am waiting for my laptop too.

---

### Post by MockY on 2009-07-07
I'm sad to say that your suggested fix did not change anything for me. I still have to increase the mouse speed in Mouse properties for it to be usable. Problem is that my regular mouse gets super fast and I have to decrease the speed once again. Very annoying.

---

### Post by damis648 on 2009-07-08
> **MockY said:**
> I'm sad to say that your suggested fix did not change anything for me. I still have to increase the mouse speed in Mouse properties for it to be usable. Problem is that my regular mouse gets super fast and I have to decrease the speed once again. Very annoying.

xorg.conf is no longer used for managing things like mice, trackpads, and keyboards. This is now done by HAL, which is what those config files I gave you were for. Remove everything you have added to xorg.conf and make sure you re-follow my directions. Regardless or not of whether the speed at all changes, SHMconfig will now be set to true, meaning you will be able to use gsynaptics.

---

### Post by MockY on 2009-07-09
> **damis648 said:**
> Regardless or not of whether the speed at all changes, SHMconfig will now be set to true, meaning you will be able to use gsynaptics.
I still get the same error when launching gsynaptics. I rebooted the computer after the settings change and install of gsynaptics.

---

