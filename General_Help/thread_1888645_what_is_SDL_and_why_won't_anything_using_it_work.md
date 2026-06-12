---
title: "what is SDL and why won't anything using it work"
date: 2011-11-29
forum: General Help
---

### Post by UmlautBanana on 2011-11-29
Darwinia, xvidcap, mupen64plus, and others complain about SDL not finding the right video device or something along those lines, then segfaults. I have all the libsdl packages (that aren't i386) installed from synaptic. Googling around, I found I might need to point SDL to X11 because it doesn't know to use that device or something, but how can I do that? Is that even my problem?

---

### Post by UmlautBanana on 2011-11-29
bump?

---

### Post by aleb on 2011-11-30
> **UmlautBanana said:**
> Darwinia, xvidcap, mupen64plus, and others complain about SDL not finding the right video device or something along those lines, then segfaults. I have all the libsdl packages (that aren't i386) installed from synaptic. Googling around, I found I might need to point SDL to X11 because it doesn't know to use that device or something, but how can I do that? Is that even my problem?

How can you tell they complain about SDL? Is there an error message printed in the console? Can you copy/paste it here?

---

### Post by UmlautBanana on 2011-11-30
Darwinia gives

```
Couldn't initialise SDL
Could not invoke gdb stack trace because path to executable not set
Segmentation fault
```

Xvidcap I uninstalled, but it gave a similar output. Mupen64plus gives

```
[blight's SDL input plugin]: Couldn't init SDL video and joystick subsystem: No available video device
```

Yeah.

---

### Post by UmlautBanana on 2011-11-30
bump again..

---

### Post by bluexrider on 2011-11-30
It us usually polite to (bump) once every 24 hours

---

### Post by gordintoronto on 2011-11-30
Here's a description of SDL: [http://www.libsdl.org/](http://www.libsdl.org/)

What version of Ubuntu are you using?

Where did you get Darwinia from?

You might want to give recordmydesktop a shot.

---

### Post by UmlautBanana on 2011-11-30
> **gordintoronto said:**
> What version of Ubuntu are you using?Oneiric.
> **gordintoronto said:**
> Where did you get Darwinia from?The latest Humble Bundle (Introversion), i.e. it's a legitimate copy.
> **gordintoronto said:**
> You might want to give recordmydesktop a shot.Thanks; worked like a charm. Not as customizable as Xvidcap, but it works. Records from microphone by default, but a quick change in pavucontrol fixed that (I wanted it to record system sound). I'd still like to get the other things (and SDL in general) working, though.

EDIT: Never mind, the GUI version is plenty customizable. So it'll work fine. The SDL problem still exists though.

---

### Post by UmlautBanana on 2011-12-03
bump?

---

