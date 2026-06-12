---
title: "Disabling 3 button mouse emulation with udev"
date: 2010-10-22
forum: General Help
---

### Post by Sworddragon on 2010-10-22
I want to disable the emulation of the third button of the mouse. I figured out with google that I have to need to write ENV{x11_options.Emulate3Buttons}="False" in a .rules file in /etc/udev/rules.d. After I created the mouse.rules and wrote ENV{x11_options.Emulate3Buttons}="False" in it the system was not complete starting after a restart with tty1. After some more search and some tryouts this is now my mouse.rules:

```
KERNEL=="mouse0", SUBSYSTEM=="input", DRIVER=="", ENV{x11_options.Emulate3Buttons}="False"

```The system is now starting without problems but the 3 button emulation isn't disabled. I'm using the development branch of Ubuntu 11.04.

---

### Post by SwiftTools on 2010-11-05
An additional way to do this is to still use xorg udev capabilities with per device tweaks.
Add a section in your xorg.conf file like the following:

```
Section "InputClass"
        Identifier "specific mouse"
        MatchDevicePath "/dev/input/event3"
        Option         "Emulate3Buttons" "False"
EndSection
```Change according to your system or simply use the following generic one:
[FONT=monospace]
[/FONT]```
Section "InputClass"
        Identifier "allmice"
        MatchIsPoniter "on"
        Option         "Emulate3Buttons" "False"
EndSection
```Now I can Rocket Jump in QuakeLive ;)

---

### Post by Sworddragon on 2010-11-17
Thanks for your help. I have found at another site a solution too to solve this problem. I have enhanced /etc/X11/xorg.conf with:

```
Section "InputClass"
    Identifier "middle button emulation class"
    MatchIsPointer "on"
    Option "Emulate3Buttons" "off"
EndSection
```

---

