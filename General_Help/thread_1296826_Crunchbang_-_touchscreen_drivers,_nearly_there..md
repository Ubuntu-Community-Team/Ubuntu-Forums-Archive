---
title: "Crunchbang - touchscreen drivers, nearly there."
date: 2009-10-21
forum: General Help
---

### Post by dchurch24 on 2009-10-21
Hi all,

...bit of background:

I have a small mini-itx box that's been knocking around for a few years - it's really my test box - if things can run ok on that machine, then they are going to be fine on my others (it's the lowest common denominator).

I have a 'home automation' system that I've been developing for the past year,and annoyingly I couldn't get the drives working under any linux distro for my touchscreen, and so I installed WinXP and wrote the front-end for that part in VB.NET.

I'd like to get rid of that machine, simply because it's the fly in the ointment. All my other machines run Linux of some flavour and the whole thing hangs together well.

The WinXP machine, despite having auto-updates turned off, sometimes reboots itself in the night, thinking that it's doing me a favour. Periodically, it will also turn on it's internal firewall which buggers up my connections to my MySQL server etc...

So, I'd dearly like to blow it out altogether.

I'm quite happy to re-write the touchscreen application for Linux (well, happy is perhaps an overstatement), but only if I can get the touchscreen working.

I followed this tutorial:

[http://www.hanckmann.net/?q=node/28](http://www.hanckmann.net/?q=node/28)

...and for the first time ever, the touchscreen is *nearly* working.

I compiled the drivers, installed, run the calibration program and when I touch the calibration targets, it detects my touch and works fine. 

The only problem is that the cursor won't actually follow my finger.

I'm so close, but so far..... ;-)

---

### Post by P4man on 2009-10-21
why do you want it to "follow your finger"? 
You mean dragging doesnt work?

---

### Post by dchurch24 on 2009-10-21
Dragging, or simply touching the screen to create a 'mouse click'.

On the existing winxp box, if I touch the screen it acts as though I have left-clicked the mouse.

On this machine, the 'beep' occurs, so I know the serial interface/drivers have detected my touch-'click', but the mouse pointer stays in the same place on the screen - i.e. not where my finger has just clicked. 

The mouse pointer ignores my screen presses.

---

### Post by P4man on 2009-10-21
ah, so its not working at all. well not as a pointing device for X anyway. 
Probably a mistake in the xorg.conf?  Perhaps post it and have a look in xorg.0.log

---

### Post by dchurch24 on 2009-10-21
Indeed! Compiling and installing the drivers has done *something* though, as my finger-presses were detected when running the calibration program.

xorg.conf:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "elo"
EndSection

Section "InputDevice"
           Identifier "elo"
           Driver "elo"
           Option "Device" "/dev/input/elo_ser"
           Option "SendCoreEvents" "true"
EndSection

```

There is no "/dev/input/elo_ser", so:

xorg.0.log:
```

(II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: elo TouchScreen)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
elo touchscreen on. local->fd ffffffff..
 After open. local->fd ffffffff
Unable to open elo touchscreen device: No such file or directorycouldn't enable device 4
SetClientVersion: 0 9
SetKbdSettings - type: -1079159380 rate: 30 delay: 500 snumlk: 252
SetGrabKeysState - disabled

```

There is, however:

by-id  by-path  event0  event1  event2  event3  event4  event5  mice  mouse0  mouse1

Could it be that I need mouse1 (presumably?) in the xorg.conf instead of elo_ser?

---

### Post by dchurch24 on 2009-10-21
Hmmmm....tried it with mouse1 and mouse0, still no joy.

---

### Post by P4man on 2009-10-21
edit: oops just a sec

---

### Post by dchurch24 on 2009-10-21
Hmmm...I ran the ./install again (remotely this time (with sudo) - I am now at work), and woohooo - the "/dev/input/elo_ser" now appears.

I have changed the xorg.conf back, but I won't know if it has worked until I get home in about an hour.

Presumably I need to restart X?

Fingers crossed!

---

### Post by P4man on 2009-10-21
> **dchurch24 said:**
> Hmmm...I ran the ./install again (remotely this time (with sudo) - I am now at work), and woohooo - the "/dev/input/elo_ser" now appears.

I have changed the xorg.conf back, but I won't know if it has worked until I get home in about an hour.

Presumably I need to restart X?

Fingers crossed!

Ah thats good news indeed. Yes you'll have to restart X.
If its not working still, run xev and see if it picks up any activity if you touch the screen.

---

### Post by dchurch24 on 2009-10-21
Hey, thanks for your help today. Much appreciated.

When I get home I'll know if it worked and I'll keep you posted! ;-)

---

### Post by dchurch24 on 2009-10-21
Well......I got home, and rebooted


...and it bloody works!

Brilliant - thanks so much for pointing me in the right direction!

---

### Post by P4man on 2009-10-21
Cool, enjoy :)
dont forget to mark this thread as solved

---

### Post by dchurch24 on 2009-10-21
Annoyingly, now I have that solved, it seems that Crunchbang isn't quite as lightweight as I'd hoped. I know it's an old machine, but XP runs fine on it, and I seem to remember xubuntu running pretty well as well.

I'll try xubuntu again (I seem to have the most luck with that) and see if it becomes useable - and of course, go through compiling the touchscreen drivers et al, all over again ;-)

Hey, practice makes perfect!

---

