---
title: "Laptop -&gt; external monitor=severe failure."
date: 2010-05-02
forum: General Help
---

### Post by marshall.robert on 2010-05-02
Hi all.

I would have thought that this would have been a key thing to work on with the ever growing laptop market. But apparently progress has fallen backwards. Though this may appear to be a bit of a rant, it is a very valid problem.

If you are a contributing developer and you think *tl;dr*, you are part of the reason that Open Source is still lagging behind.

Here is what happened:

My laptop is my only machine, I use it as a desktop by plugging in an external monitor along with a keyboard and mouse and sound system. I have been doing this for 2 years now. Whilst this works flawlessly in every version of Windows (with it automatically detecting and applying the correct resolution) I have had on here, there continues to be problems with Ubuntu (I can't comment on other versions of Linux since this is the only one I really use).

Previous problems used to include not even being able to switch to an external monitor without rebooting with it plugged in because it wouldn't detect otherwise. Later on I could switch by using the special fn key; there were still resolution problems though, most of which are current. Another problem is with Gnome Panel; it fails to keep the order of its widgets after changing resolution, everything is in an apparently random new position.
Now while I hoped it would be improved in this new Ubuntu 10.04, I expected it to be the same. But I was yet to be disappointed. Upon plugging in the monitor and pressing the fn key twice to get the output only on the external monitor, I am met with the usual 1280x800 resolution of my laptop screen panning over a 1024x768 actual resolution. My monitors native resolution is 1680x1050. Since I expected this I fired up nvidia-settings and changed the necessary options to set the desktop resolution to the native resolution of my external monitor.

All is now fine. Then I unplugged the monitor, used the fn key to switch back. I expected it to behave as before, switch back to my laptops native resolution. But this time, it didn't. It stayed at 1680x1050. I was unable to set it back with nvidia-settings either because it still thought the native resolution was that of my external monitor. I fired up the gnome-display-properties and attempted to use that; and it worked, to an extent. I got my laptops resolution back but things like the Gnome Panel were still out of place, and compiz wasn't rendering properly and was leaving bits of windows and menus everywhere. I managed to get around restarting X (I was unable to log out because the panel applet was hidden beyond my laptops resolution) only to find that my video drivers had crashed. This caused compiz to use a whole core of my CPU and not render any effects. I killed compiz and then everything went black, things came back as they updated as well as a 32x32 trail of where my cursor had been.

Ubuntu now can't boot.


How long is it until Ubuntu gains the ability to automatically detect, and switch to at the correct resolution, an external monitor and come back again without there being a total muck up? This is something that is long overdue. And it is certainly something that is preventing me from using Ubuntu as my main OS. I beg you, please do something about it.

Suggestions on how to get around this, until it is fixed, are very welcome and will be greatly appreciated.

-Rob

---

### Post by frogotronic on 2010-05-02
1) Don't use the Fn+whatever key for external monitors.  They rely on EDID which for all intensive purposes is a Windows only functionality.  Use the nvidia-settings panel.

2) boot with a liveCD and fix your Xorg.conf file.

You should be good.

---

### Post by dino99 on 2010-05-02
is it a fresh install or a dist-upgrade ?

is it your old xorg.conf upgraded ?

which graphic on board ?

---

### Post by marshall.robert on 2010-05-02
> **cement_head said:**
> 1) Don't use the Fn+whatever key for external  monitors.  They rely on EDID which for all intensive purposes is a  Windows only functionality.  Use the nvidia-settings panel.
I'm not going to stop using that key, for what I can see it does its job; tells the OS to make the switch. And EDID is a VESA standard.

> **cement_head said:**
> 
2) boot with a liveCD and fix your Xorg.conf file.

You should be good.
Thanks for the suggestion, will do.

> **dino99 said:**
> is it a fresh install or a dist-upgrade ?

is it your old xorg.conf upgraded ?
Fresh.

> **dino99 said:**
> which graphic on board ?
It's an nVidia 8600M GT. It is a dedicated board (not onbard like most laptop chips).


My main point here is: this shouldn't have happened in the first place, this functionality should have been well established in Linux by now.

---

### Post by MdaG on 2010-05-20
I just want to agree with the original poster here. I have the same problem at work and being the only Linux user among Mac and Windows users I'm basically standing out as the Linux guy who  won't let go of technology "that just doesn't work".

---

### Post by dreamr on 2010-06-02
Yep, same here. I've effed up already couple presentations when my Ubuntu laptop just became unusable after trying to switch to an external monitor. It just doens't work in that direction. Switching back to single monitor works for me though.

This was a problem already in Karmic 9.10, but there I could get past the problem by turning Compiz/visual effects off while making the switch. Not doing so caused the whole system to crash. But seems that doesn't help anymore... no matter what I do, getting external monitor to work with a workable system running requires a reboot (maybe re-login is enough, have to try that).

And about the Xorg.conf, my understanding was that Ubuntu switched into something new in Karmic, and Xorg.conf isn't used any more by default? At least I don't have the file any more.

Last time it worked for me was in Jaunty 9.04.

---

### Post by dreamr on 2010-06-02
Okay, tried it and it seems to work.

So quickest way to switch to an external monitor seems to be through re-login. Not really ideal solution, but beats a reboot.

---

### Post by the hoplite on 2010-07-20
hi guys, been reading these and similar posts because I had the same problem. I tried out pretty much everything to get a more direct way of switching the external monitor on and off.
Well, not the simplest one. I just configured my xorg.conf (through nvidia-settings, must use sudo) to the external monitor, with the laptop one switched off. So now I got it working right from the boot, and if it isn't attached, well, the graphic driver falls back to the safe mode and turns on the laptop monitor. Perfect for my needs.

---

### Post by righdforsa on 2010-11-02
Just found "disper" and I am so glad I finally found a solution to this problem. Run this from the command line:

```
sudo apt-get install disper
```

Then, to switch between primary display (laptop screen) and secondary display (external monitor) do:

primary display
```
disper -d auto -s
```

secondary display
```
disper -d auto -S
```

Rock on!

---

### Post by Schuby007 on 2010-11-02
Hi,

I'm having similar problems! I've installed Ubuntu 10.04 64-bit on my Alienware m15x laptop. The laptop has an Nvidia GeForce 8800M GTX gpu; I'm using NVIDIA Driver Version: 195.36.24 (recommended by "Hardware Drivers").

At home I connect my laptop to my external monitor via HDMI and use the external by itself. In order to get the external display working I had to enter Nvidia settings and enable the external display and then disable the laptop display and restart. I then had to edit gnome power settings to set lid-close action to "Do Nothing" so my external monitor won't go blank when I close my laptop screen. This is fine for when I'm working at home...

The problem is when I have to change locations... I have to enter nvidia-settings, enable the laptop display, disable the external display and restart. It's a royal pain in the ***... 

Is there no way to automate Ubuntu so that if I unplug my external display it will switch to my laptop screen and vice versa? Like the original poster mentioned: this works great in Windows it would be really awesome if Ubuntu could do it too.

BTW I saw your post righdforsa and I will check out that "disper" program.

Another thing...
I've noticed that neither the screensaver nor the gnome-power-manager "put the display to sleep" functions will work on my external if my laptop "lid" is closed. I've done a lot of searching on the interwebs and I can't find a solution. It seems to me that the gnome-screensaver and power management are  getting confused between my internal and external monitors. Perhaps it  could be because display settings are handled by nvidia-settings?? If  thats the case then I consider it bad practise for Ubuntu to include the  proprietary nvidia drivers without proper support.

I'd be very interested in knowing if anyone else is having this problem. And would be thrilled if anyone had any solutions.

Thankyou.

my xorg.conf file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Dell Alienware2210"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800M GTX"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection 
```

---

