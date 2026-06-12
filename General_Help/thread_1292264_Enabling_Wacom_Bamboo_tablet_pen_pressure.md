---
title: "Enabling Wacom Bamboo tablet pen pressure"
date: 2009-10-15
forum: General Help
---

### Post by jarame on 2009-10-15
This should be the last "help" thread I post, lol. I'm learning as I go along, and that's what really matters, right? Haha, okay so onto the purpose of this thread:

**My issue:** I went through all the trouble of searching these forums and google searching on how to install Wacom Tablet drivers. I seem to have the drivers installed but for some reason in Photoshop I cannot enable Pen Pressure, but it works like it's supposed to in GIMP.

**My question: **How can I enable the pen pressure for my Wacom Bamboo pen tablet?

And just to clarify everything up i've been to these sites and yet to find an answer:

[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+tools](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+tools)
&
[https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver)

I can't figure out how to get to the "Configure Mouse" settings as described in the tutorial of the first site. And the second site just helped me install the drivers, but nothing about pen pressure.

---

### Post by jarame on 2009-10-15
bump!

---

### Post by Favux on 2009-10-15
Hi jarame,

Since pressure works in Gimp it sounds like you've set up the Bamboo correctly.

I assume you've set up Photoshop through wine.  So it's probably a wine configuration problem.

---

### Post by jarame on 2009-10-15
> **Favux said:**
> Hi jarame,

Since pressure works in Gimp it sounds like you've set up the Bamboo correctly.

I assume you've set up Photoshop through wine.  So it's probably a wine configuration problem.

I guess I did, but the eraser part on my pen doesn't erase...my pen is now a dual-sided pen, lol. But at least the pen pressure works in Gimp. And yes, i set up photoshop through wine, but it was an older version of Wine (version 1.1.18). Maybe I should try setting it up with a newer version of Wine?

---

### Post by Favux on 2009-10-15
Hi jarame,

Sorry but I don't know anything about wine.  I think it had trouble with the newer Photoshop and does better with the older version (CS3?).  So trying the newest wine makes sense to me.

See near the bottom of here to setup eraser in Gimp:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by jarame on 2009-10-15
> **Favux said:**
> Hi jarame,

Sorry but I don't know anything about wine.  I think it had trouble with the newer Photoshop and does better with the older version (CS3?).  So trying the newest wine makes sense to me.

See near the bottom of here to setup eraser in Gimp:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)


Thanks. I'm still so confused as to what should be edited. My tablet worked when I first plugged it in, but the pen pressure didn't work, so I installed Wine then the Pen pressure worked in Gimp and not PS. -sigh- I guess I'll just deal with it, lol. Thanks again though Favux

---

### Post by Favux on 2009-10-15
Hi jarame,

I can talk you through setting up the Bamboo in Jaunty.

In a terminal enter:
```
xinput --list
```
And let's see what the output is.

---

### Post by jarame on 2009-10-15
> **Favux said:**
> Hi jarame,

I can talk you through setting up the Bamboo in Jaunty.

In a terminal enter:
```
xinput --list
```And let's see what the output is.

```
jarame@ubuntu:~$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=3    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Logitech USB-PS/2 Optical Mouse"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"Wacom Bamboo eraser"    id=6    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Bamboo cursor"    id=7    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Bamboo pad"    id=8    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 4
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 4 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 71
        Resolution is 1
"Wacom Bamboo"    id=9    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
```

That's what I have

---

### Post by Favux on 2009-10-15
Hi jarame,

That looks standard for Jaunty.  Did you check in Synaptic Package Manager if wacom-tools was also installed?

If things do what you want you can leave it alone.  If you want to do more configuring see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

---

### Post by jarame on 2009-10-15
> **Favux said:**
> Hi jarame,

That looks standard for Jaunty.  Did you check in Synaptic Package Manager if wacom-tools was also installed?

If things do what you want you can leave it alone.  If you want to do more configuring see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Yeah wacom-tools is installed. I followed some tutorial on how to get updated Wacom drivers for Ubuntu Jaunty. Everything BUT the eraser and pen pressure in Photoshop works. So I guess I'm just stuck with Gimp or rebooting into Windows since I'm so dang picky, lol. Thanks for your time :] I appreciate it

---

### Post by Favux on 2009-10-15
Hi jarame,

Ok, I misunderstood.  You compiled and installed a newer linuxwacom than the default 0.8.2-2 in Jaunty?  Then the .fdi in the site I linked probably wouldn't work for you.

---

### Post by jarame on 2009-10-16
> **Favux said:**
> Hi jarame,

Ok, I misunderstood.  You compiled and installed a newer linuxwacom than the default 0.8.2-2 in Jaunty?  Then the .fdi in the site I linked probably wouldn't work for you.

yeah I installed 0.8.4-3 cause it was the newer version. Maybe I should update Wine later as well, might be some coding between the newer versions that coincide with each other, who knows? lol Thanks for your help man!

---

