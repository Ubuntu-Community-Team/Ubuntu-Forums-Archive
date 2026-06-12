---
title: "Screensaver Locking/Freezing Computer"
date: 2006-04-03
forum: General Help
---

### Post by bg_27 on 2006-04-03
I have been having problems with my screensaver locking/freezing my computer, i cant do anything, basically it requires a hard reboot. Can't log in remotely either during this freezing.

The freezing started occuring when i upgraded my video driver to the xorg-driver-fglrx. The screensavers worked prior to this driver upgrade, but now whenever the screensaver is activated the machine freezes, i can't even go to the screensaver control panel in preferences, that also instantly freezes the computer. 

Here is my fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000/9100 PRO IGP Series DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

thanks

---

### Post by nanotube on 2006-04-03
well, dont know how to help you with the video driver, but to prevent the screensaver from starting up and crashing stuff, here is what you do:
go to your home directory, and find a file there named ".xscreensaver"
open it up with your favorite editor, and change the line that starts with "mode:" to look like this:
```
mode:		blank
```
this will make screensaver simply blank the screen, rather than start some fancy saver, thus (very probably) preventing it from freezing. 
if that doesnt work, there is another alternative. open the gconf editor (applications>system tools>config editor), and uncheck the following item: /apps/gnome_settings_daemon/screensaver/start_screensaver
that will prevent the screensaver from even starting when you log in.

these tips should at least take care of the crashing.. which is a big step up. :)

---

### Post by encompass on 2006-04-03
Your crashes may be part of a bad video driver... I had that issue and went to eh vesa driver because I wanted stability more than graphics.

---

### Post by bg_27 on 2006-04-03
I am at work so i can't test this, but i ran the command:

xset s off

Does that also disable the screensaver?

Thinking back to when these problems first happened, after upgrading the video drivers i went to the screensaver control panel and it said that the screensaver daemon wasn't started, and that it was going to start it, it tried to start but then it froze.


These vesa drivers you speak of, are they compatible with ATI?

---

### Post by nanotube on 2006-04-03
yes, vesa is ati-compatible, but does not do any fancy 3d acceleration and stuff.
and afaik, the xset command should be equivalent to turning off the saver. but i dont think that will get saved on reboot.

---

### Post by antiemptyv on 2006-04-03
i was having a similar problem which seemed to be fixed when i switched from gnome to fluxbox only sd my desktop manager.  just an idea, and it's way more speedy, too!

---

### Post by flankker on 2006-04-03
[QUOTE=bg_27]I have been having problems with my screensaver locking/freezing my computer, i cant do anything, basically it requires a hard reboot. Can't log in remotely either during this freezing.

The freezing started occuring when i upgraded my video driver to the xorg-driver-fglrx. The screensavers worked prior to this driver upgrade, but now whenever the screensaver is activated the machine freezes, i can't even go to the screensaver control panel in preferences, that also instantly freezes the computer. 

Here is my fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000/9100 PRO IGP Series DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

thanks[/QUOTE]

i had the exact same problem as u, with the exact same card. the problem is the ati driver. 

just switch to the vesa drivers. the ati drivers dont support hardware acceleration for our card so u wont be missing anything.

---

### Post by Pinkshie on 2006-04-03
I have the same problem and have an ATI Radeon 7000/VE
How do I get these vesa drivers?

PLease bear in mind that I am hours new to ubuntu and linux in general

---

### Post by nanotube on 2006-04-03
hey pinkshie,
edit your /etc/X11/xorg.conf file, by typing command 
```
sudo gedit /etc/X11/xorg.conf
```
at the terminal, and change the line 
```
        Driver          "ati"
```
to 
```
        Driver          "vesa"
```
save the file,
and then restart X (or even your whole computer, if you feel like it).
that will start using vesa instead of the ati driver. just note that it will provide to 3d acceleration... but if that's not important to you, then no problem.

---

### Post by Pinkshie on 2006-04-04
Strange...
there is absolutely nothing in my /etc/X11/xorg.conf file to change.
Do you think it could be somewhere else?

---

### Post by nanotube on 2006-04-04
is your xorg.conf file blank??

---

### Post by Pinkshie on 2006-04-05
Ah it's sorted! I forgot to put vi in command sudo vi /etc/X11/xorg.conf. ](*,) 
I replaced the driver for vesa and everything works wonderfully now!

Many thanks for your help.

---

### Post by bg_27 on 2006-04-05
Yep, changed the driver to "vesa" and i have no lokcing up anymore, and i have seen no other side effects

---

### Post by nanotube on 2006-04-05
excellent. :)

---

### Post by bg_27 on 2006-04-05
whats stupid is that i found these sets of instructions multiple times while searching google for this problem:

[http://lug.wsu.edu/node/431](http://lug.wsu.edu/node/431)

---

### Post by Pinkshie on 2006-04-09
Ah yes I did come across that but none supported my card which is ancient and cheap (7000 VE). It might just be time to make an investment in a new video card anyway...

---

### Post by jazzmuzik on 2006-04-11
Ditto to the OP: Lockups related to the "faster" ati drivers. Can't do anything but press reset.

Is is odd that the ati driver install program ends up putting references to two video drivers into xorg.conf? Here's an excert from mine:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection
```

---

### Post by nanotube on 2006-04-11
[QUOTE=jazzmuzik]Ditto to the OP: Lockups related to the "faster" ati drivers. Can't do anything but press reset.

Is is odd that the ati driver install program ends up putting references to two video drivers into xorg.conf? Here's an excert from mine:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection
```[/QUOTE]

hmm, that does seem weird to me... but i havent played with the fglrx driver myself, since my card worked out of the box on the built-in ati driver, i have not had the desire to screw around with it. so maybe i am wrong on this account. ;)

---

