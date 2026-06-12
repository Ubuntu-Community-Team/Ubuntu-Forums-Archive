---
title: "Two finger scroll Ubuntu 11.04"
date: 2011-09-14
forum: General Help
---

### Post by ernestj on 2011-09-14
I have been trying to figure out how to enable two finger scroll. I looked in the Mouse preferences and only have to tabs for options. In  my search, I have seen three choices or tabs. In the third tab are to enable two-finger scroll. What do I need to do to add more mouse options or can I add a command in terminal to enable two finger scroll. I have an ASUS.

Thanks

---

### Post by papibe on 2011-09-14
Do you really need two finger scroll? I ask because I believe regular scroll is enable by default on 11.04. I'm using it like this: one finger moves vertically on on very left part of the track pad.

Regards.

---

### Post by ernestj on 2011-09-14
I do not have even one finger scroll. I was using Windows 7 and liked the ability to two finger scroll. I do not like Windows 7 however. 
I believe I am missing the an option in Mouse Preferences. I have a "General" tab and a "Accessibility" tab and that is it. I have read that there is a third tab and that would enable scrolling. I know it has been done. Have not figured out how to do it.

---

### Post by papibe on 2011-09-15
> **papibe said:**
> ...on very left part of the track pad.
Oops, the scroll works in the right side of my track pad.

---

### Post by Governa on 2011-09-15
I want to activate two finger scroll on my Dell Latitude D620 (UK model, if relevant). I believe it uses a Synaptics touchpad (please correct me if I'm wrong).

Is there any GUI based app that allows me to configure the trackpad? I had to manually add new configurations to xorg because Ubuntu's default Mouse config menu doesn't really allow me to config the speed to my liking (too slow in max). I found a topic that helped me correct that by editing xorg.

I checked qsynaptics and others but they were either not user friendly, broken in 11.04 or discontinued. Any suggestions?

---

### Post by papibe on 2011-09-16
Just in case, this is my mouse entry in my xorg.conf:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```
Regards.

---

### Post by madjr on 2011-09-16
you guys referring to natural scroll?

[http://www.omgubuntu.co.uk/2011/07/reverse-natural-scrolling-ubuntu-os-lion/](http://www.omgubuntu.co.uk/2011/07/reverse-natural-scrolling-ubuntu-os-lion/)

---

### Post by Governa on 2011-09-16
No, two finger scroll works like this:

[IMG]http://2.bp.blogspot.com/_ZKz0HLBzel4/TKzf4whXJaI/AAAAAAAAAMw/Ksv2pVs-UqQ/s1600/00-Two-Finger-Scroll.jpg[/IMG]

I'm just very used to do it on my Macs.

---

### Post by just_jeepin on 2011-09-20
I too would like to get this working.  I'm on a Dell Latitude D600 with Ubuntu 11.04.  I've clicked two finger scrolling but it does nothing.

---

