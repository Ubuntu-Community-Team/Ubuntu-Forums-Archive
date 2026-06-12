---
title: "3 questions about xorg.conf and gsynaptics"
date: 2010-08-15
forum: General Help
---

### Post by ptoche on 2010-08-15
I'm having problems configuring my synaptics touchpad. I'm on a clean Kubuntu 10.4 install. I am quite possibly missing the correct drivers. There are several threads devoted to the problem, but so far I can't seem to find instructions that will match my system.

I understand that one way is to install gsynaptics and configure the xorg.conf file. However, I don't have a xorg.conf file. But I do have, in its place, a failsafe version of the file (whatever that is). And it seems to list the wrong driver. 

Here is my xorg.conf.failsafe :

```


     Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection 


```1. I have read that ksynaptics is no longer up to date and that gsynaptics is the way to go even on kubuntu, correct?

2. I have read that xorg.conf files aren't necessarily present anymore in the latest kubuntu systems. But one could be created for the specific purpose, would that be the best way to go?

3. What is the failsafe xorg.conf file I have on my /etc/X11 folder? Is it doing the work of xorg.conf, is it needed, can/should it be modified?


and, lastly, 

 some have reported that xserver-xgl interferes with the driver, is that  so? should I uninstall it? (I don't really understand if it's needed on  my system).

Thanks!


Selected References:
[http://ubuntuforums.org/showthread.php?t=917988&highlight=gsynaptics](http://ubuntuforums.org/showthread.php?t=917988&highlight=gsynaptics)
[http://ubuntuforums.org/showthread.php?t=1220423&highlight=gsynaptics](http://ubuntuforums.org/showthread.php?t=1220423&highlight=gsynaptics)
[http://ubuntuforums.org/showthread.php?t=1314919](http://ubuntuforums.org/showthread.php?t=1314919)

---

### Post by bobcollard on 2010-08-15
Install gpointing-device-settings instead.  both ksynaptics and gsynaptics are being outdated.

---

### Post by ptoche on 2010-08-15
okay, thanks, I'll do that, and report back soon.

[http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

---

### Post by bobcollard on 2010-08-15
If I remember correctly Ubuntu Gnome has two boxes under System/Mouse/touchpad that needs to be unchecked for anything third party to work.  Might take a restart.  You can put gpointing-device-settings in your startup applications to have it on hand at reboot.

---

### Post by ptoche on 2010-08-16
So I've installed gpointing-device-settings and it does all the things advertised. Unfortunately I haven't been able to solve my problem. This may simply be a reflection of my inability to find the correct settings from withing gpointing-device-settings or elsewhere. Some help would be greatly appreciated. So let me describe the problem in some detail.

I have more clearly identified the origin of the touchpad's misbehaviour:

**The cursor jumps about whenever the touchpad is touched twice in quick succession **(but not if the delay between touches is longer, e.g. more than about 1 second). 

This is probably also responsible for tabs switching frantically and loopingly whenever the pointer hovers above them. 

I have disabled tapping and therefore use the left-click button to select. However, by design, the left-click button is just the bottom-left portion of the touchpad and as such behaves like the rest of the touchpad, so that if I touch the left-click area with my left hand, while using the right hand to guide the pointer from the main area of the touchpad, well the touchpad interprets this as a double-touch.

What happens when I double-touch the touchpad? Suppose I am guiding the pointer to the right-hand side of the screen, by stroking the right-hand side of the touchpad with my right index finger. Suppose then that I lift my right index finger for a fraction of a second and then touch the left-hand side of the touchpad with my left index finger. Then, the pointer jumps immediately to the left-hand side of the screen, as if my right and left index fingers were indicating the start and finish points of a trajectory across the screen.

Why would I touch the touchpad twice in succession if I didn't intend to do something funny? As I said above, the left-click button on my laptop is part of the touchpad so that if my left index finger prepares itself for an innocent, pedestrian click, the software interprets the first contact with the touchpad as a stroke, before correctly interpreting the pressure as a click. Result: I click all over the place except on my target.

I would return this HP-DV6-3048TX immediately if it weren't a birthday gift from my wife...

---

### Post by bobcollard on 2010-08-16
An alternative would be buy a small mouse and disable the touchpad with gpointing-device-settings.  My Dell has actual buttons so I don't have this problem, but, since I use a wireless keyboard and mouse with an external monitor, the computer became a desktop with the battery removed unless traveling.  I know people have different uses for their computer and I sympathize with your problems.

---

### Post by ptoche on 2010-08-20
> **bobcollard said:**
> An alternative would be buy a small mouse and disable the touchpad with gpointing-device-settings.

thanks for your suggestion Bob, but mine is a laptop. I have just invested in a super small power adaptor (from Kensington) because the original 120W HP adaptor is too heavy -- I don't want carry a mouse around, however small. What I've done instead, until I find a better solution to the touchpad, is to disable it completely and assign the left-window key to right-click and the right-contextmenu key to left-click, both being conveniently located for the purpose (or perhaps the opposite, I'm suddenly confused about the meaning or right-clicking and left-clicking).


> **bobcollard said:**
> My Dell has actual  buttons so I don't have this problem

so does mine! and it is sufficiently small that it doesn't get brushed while typing, so it doesn't even require a touchfreeze tweak. But when I purchased my new HP I was focusing on all the things my Dell had got wrong and didn't foresee this touchpad nightmare...

---

### Post by ptoche on 2010-08-26
I solved my problem, 

[http://kubuntuforums.net/forums/index.php?topic=3113349.msg239420#msg239420](http://kubuntuforums.net/forums/index.php?topic=3113349.msg239420#msg239420)

---

