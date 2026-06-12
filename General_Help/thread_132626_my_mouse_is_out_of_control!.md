---
title: "my mouse is out of control!"
date: 2006-02-18
forum: General Help
---

### Post by breakerfall on 2006-02-18
hey all...

i dont normally shout for help, but this is driving me crazy...

i have kubuntu (had ubuntu) installed on my averatec laptop, running great, been running for a few months now...

every now and then, i get the urge to try to slow down my touchpad, because it is so unbelievably fast that i have to concentrate to control it...
i have the same problem when i plug in a usb mouse, only worse...
i have tried to tweak the x config file, but i read somewhere that mouse accelleration stuff in xorg isnt controlled by xorg.conf... my mouse accelleration is all the way down in the the mouse control panel and still i need it slower...

in windows, i have the pointer set about in the middle of the slider (for reference)

any ideas?

thanks,
mike

---

### Post by cilynx on 2006-02-18
I have a wonky touchpad and use xorg.  Without this config, my touchpad is terribly slow.  Not the same problem, but maybe the same solution...

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "ClickTime"             "0"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "10"
        Option          "HorizScrollDelta"      "10"
        Option          "MinSpeed"              "0.45"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.020"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "0"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        Option          "SHMConfig"             "true"
EndSection

```

If nothing else, it's a good starting point...

Edit:

Oh yeah.  If you don't like the side / bottom scrolling, just cut those lines out or set their width to "0"

---

### Post by hyperpsyched on 2006-02-18
Try this link:

[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)

It runs through getting an ALPS touchpad working and with this thread you can at least figure which touchpad you have and work from there.

Do not forget to backup your /etc/X11/xorg.conf file before you go changing settings. If you do not know how then do this...

sudo cp /etc/X11/xorg.config /etc/X11/xorg.config_backup

... that way if something goes wrong then you can revert like this

sudo cp /etc/X11/xorg.config_backup /etc/X11/xorg.config

... but you probably already knew that.

Read the thread above, you will learn a ton about configuring your touchpad. Once you get a feel for what each setting does you will never use a graphical configurattion tool (I was using ksynaptics but it never seemed to work for me). Good luck. 

Oh and if mouse speed is the issue look at the options called

MaxMouseSpeed and MaxMouseAccel or something like that...

Good Luck.

---

### Post by hyperpsyched on 2006-02-19
Actually it was "MaxSpeed" and "AccelFactor" affecting mouse speed, as i the config file above.

---

