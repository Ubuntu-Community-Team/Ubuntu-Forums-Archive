---
title: "Open program on startup in minimized state"
date: 2010-02-02
forum: General Help
---

### Post by senyaq on 2010-02-02
Hi all!

I already know how to make a program load when you log in
System -> Preferences -> Startup Applications
And I know how to make RhythmBox minimize to the top taskbar
You just close the window, as opposed to quitting the program altogether
But does anyone know how to open RythmBox on startup in its taskbar state?

I'm assuming this may be parameters at the end of the command
I don't actually want it to open in the minimized state
Because this would just minimize it to the lower taskbar
I actually mean "minimized" to the little icon in the top right hand corner

any ideas? thanks in advance!

SQ

---

### Post by ImperialXT on 2010-02-02
rhythmbox-client --hide

found this using man rhythmbox-client

---

### Post by senyaq on 2010-02-03
nope, that doesn't work. it still opens in its restored state.

---

### Post by stinkeye on 2010-02-03
Change the status icon plugin to *owns the main window*

---

