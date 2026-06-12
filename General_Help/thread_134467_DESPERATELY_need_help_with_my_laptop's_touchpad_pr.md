---
title: "DESPERATELY need help with my laptop's touchpad problem!! Please."
date: 2006-02-21
forum: General Help
---

### Post by duckdown on 2006-02-21
For the love of God, can someone PLEASE help me..  People on IRC are very unhelpful towards a new user, and I don't have a clue how to fix this.

I just installed Dapper 4, and everything is working great, except for my touchpad.

I own a Dell D600 Laptop, and I have KDE installed, but when I am in X/KDE my touchpad is moving EXTREMELY slow.  It takes over 10 strokes on the touchpad just to move the cursor from one side of the screen to the other.

I am not sure what kind of touchpad it is, but xorg.conf says its a synaptics.  One nice person on IRC pasted me their section from xorg.conf and I have tried it, but it didn't speed it up even in the least.

My original xorg.conf looked like this (After install):
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection


The person from IRC pasted me this one:
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "100"
        Option          "MinSpeed"              "0.06"
        Option          "MaxSpeed"              "0.12"
        Option          "AccelFactor"           "0.0010"
        Option          "SHMConfig"             "on"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "0"
        Option          "TapButton3"            "0"
        Option          "FingerHigh"            "35"
EndSection



It did not fix the problem even in the SLIGHTEST.. Can someone PLEASE tell me what to do.  Maybe my touchpad isn't a synaptics; how am I supposed to tell?  I desperately need this fixed, I am about to tear my entire head of hair out.

Thanks in advance

---

### Post by dcstar on 2006-02-22
[QUOTE=duckdown]For the love of God, can someone PLEASE help me..  People on IRC are very unhelpful towards a new user, and I don't have a clue how to fix this.

I just installed Dapper 4, and everything is working great, except for my touchpad.

I own a Dell D600 Laptop, and I have KDE installed, but when I am in X/KDE my touchpad is moving EXTREMELY slow.  It takes over 10 strokes on the touchpad just to move the cursor from one side of the screen to the other.
......[/QUOTE]
You may be better served in the Dapper/KDE forums.

This is the Breezy-Gnome forum.

---

