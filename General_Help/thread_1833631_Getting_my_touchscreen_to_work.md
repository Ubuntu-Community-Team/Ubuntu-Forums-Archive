---
title: "Getting my touchscreen to work"
date: 2011-08-26
forum: General Help
---

### Post by Felystax on 2011-08-26
Hi,

I have got a Terra all in one pc 1910, which has a touchscreen. I am running ubuntu 10.04 on it, and i'm trying to get the touchscreen to work. The machine does recognize touch, except the calibration is extremely off. I would like to get this to work, except I don't know how to do it. I've tried various programs, such as xinput_calibrator, but xinput says there's nothing to calibrate. No other programs seem to cut it. However, I do believe it is possible to calibrate the touchscreen, since it does respond to touch input. Could anyone please inform me of a way to do this?

Thanks in advance!

---

### Post by raja.genupula on 2011-08-26
[http://liliputing.com/2011/03/ubuntu-11-04-gets-touchscreen-friendly-love-handles.html](http://liliputing.com/2011/03/ubuntu-11-04-gets-touchscreen-friendly-love-handles.html)

---

### Post by Brucevdk on 2011-08-27
I don't have a 	TERRA All-In-One PC 1910 but I do have a ThinkPad X61 tablet which has a resistive Wacom touchscreen. In my case there's three devices: 1 for the stylus, 1 for touch and 1 for the eraser. The stylus works perfectly out of the box, but touch isn't calibrated correctly.

I'm not aware of a program that helps with the calibration but in my case the following calibrates the touch device properly (I was lucky enough that somebody else had already published these numbers):

```
xsetwacom set "Serial Wacom Tablet touch" topy "85"
xsetwacom set "Serial Wacom Tablet touch" topx "51"
xsetwacom set "Serial Wacom Tablet touch" bottomx "933"
xsetwacom set "Serial Wacom Tablet touch" bottomy "957"
```

You can use `xsetwacom --list` to list the available devices.

And I've made these changes permanent by having a `xorg.conf` that contains:

```

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"      "/dev/input/wacom"    
    Option        "Type"        "cursor"
    Option        "USB"         "on"        
    Option        "ForceDevice" "ISDV4"        
EndSection


Section "InputDevice"
    Driver        "wacom"
    Identifier    "touch"
    Option        "Device"      "/dev/input/wacom"  
    Option        "Type"        "touch"
    Option        "ForceDevice" "ISDV4"               
    
    # Manual calibration for making finger touch more precise
    Option      "TopX"          "85"
    Option      "TopY"          "51" 
    Option      "BottomX"       "933"
    Option      "BottomY"       "957"
EndSection


Section "ServerLayout"
    Identifier      "Default Layout"
    Screen          "Default Screen"

    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice     "touch"     "SendCoreEvents"  
EndSection


```

If you don't have a Wacom touchscreen I'm not sure if any of this helps.

---

### Post by Favux on 2011-08-27
Hi Felystax,

If your touchscreen is usb we should be able to find out which one it is in the output in a terminal of:
```
xinput list
```
I'm surprised xinput_calibrator isn't seeing anything to calibrate if the touchscreen is in fact responding.  I would think then at least the evdev X driver is running the touchscreen and xinput_calibrator would pick it up.  Evdev is the fallback driver that tries to pick devices up that haven't been matched to another driver.

---

