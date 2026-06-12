---
title: "Run Program vs. Run Application"
date: 2009-07-29
forum: General Help
---

### Post by theGlitch on 2009-07-29
I recently upgraded my Ubuntu to 9.04 and deleted what I deemed to be unnecessary (including evolution). I add a few of the norms and dropped in some of the config files from my old installation.

Somewhere in all of that ALT+F2 got set to Run Program instead of Run Application. I've been able to map Run Application to ALT+F3, but would prefer to keep it with what i'm used to.

I'm prepared to switch to Gnome-do if I *HAVE* to. But again, I'd rather keep to what I've been doing. Thanks in advanced!

---

### Post by theGlitch on 2009-07-30
bump

---

### Post by lisati on 2009-07-30
Technically there is very little difference (if any) between running an "application" and running a "program" - the word "application" usually refers to the same thing as "program". Have a look here: [http://en.wikipedia.org/wiki/Application_software](http://en.wikipedia.org/wiki/Application_software)

---

### Post by theGlitch on 2009-07-30
I know there is no difference between the words application and program. But there is quite a bit of difference between the launchers.

Run program is very similar to Windows' run function where you must know exactly what you're looking for. That means you need to know exactly how to spell the executable name.

Run application will predict for you if you don't know exactly how to spell it (or don't want to finish writing the word). I know I can get this functionality with gnome-do and have tried it; but I like run application better.

---

### Post by theGlitch on 2009-08-07
bumped

---

### Post by gerber on 2009-08-13
does anyone have a solution for this?

---

### Post by gerber on 2009-08-13
This seems to work:

Go to System -> Preferences -> Keyboard Shortcuts

Remove the "Alt+F2" shortcut for the "Show the panel's 'Run Application' dialog box" action (by clicking on the "Alt+F2" shortcut and pressing backspace).

Click the "Add" button and enter the following:
Name: "show run application dialog" (some arbitrary description actually, no quotes)
Command: "gnome-panel-control --run-dialog" (without the quotes)

Hit "Apply" and it should work now.

---

### Post by theGlitch on 2009-09-03
Thank you very much! I didn't think anyone had answered it (the forum's email notification isn't working)

---

