---
title: "Dosbox shows splash screen, then quits?"
date: 2010-01-10
forum: General Help
---

### Post by Don Scapp on 2010-01-10
I am trying to run Dosbox on 9.10, and both the Software Centre isntallation, aswell as DBGL's included version of Dosbox load the splash screen, then promply quit. I have had success with previous ubuntu versions, and am wondering why I can't get any further on the new version?

---

### Post by rCXer on 2010-01-10
Apparently there's an error.  Can you run dosbox in the terminal...
```
dosbox
```
...and post the output.

---

### Post by Don Scapp on 2010-01-10
Ahhh, thanks for that, it must be the soundblaster card causing conflicts (I use a second card for the gameport, but ubuntu hasn't detected the gameport gamepads I have and I've never known how to set Gravis Gameport pads up.)

> DOSBox version 0.73
Copyright 2002-2009 DOSBox Team, published under GNU GPL.
---
CONFIG:Loading primary settings from config file /home/trevoo/.dosbox/dosbox-0.73.conf
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss
Two or more joysticks reported, initializing with 2axis
Using joystick Microsoft Microsoft SideWinder Plug & Play Game Pad with 2 axes, 6 buttons and 0 hat(s)
Using joystick Microsoft Microsoft SideWinder Plug & Play Game Pad with 2 axes, 6 buttons and 0 hat(s)

It HAS detected my two usb pads though, but why it gets no further than that doesnt make any sense? Can I disable the midi port in ubuntu?

---

### Post by rCXer on 2010-01-10
Hmm no errors.  You should try posting your problem at [dosbox forums]("http://vogons.zetafleet.com/index.php?c=7"). They'll know what to do next.

---

### Post by Don Scapp on 2010-01-11
Thanks ever so much, I'll post there, and I might try changing the midi settings in the conf file, or just disabling the midi port card all together.

Thanks for your help!

---

