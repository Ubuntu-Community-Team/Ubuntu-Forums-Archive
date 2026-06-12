---
title: "Not able to rotate screen"
date: 2009-10-25
forum: General Help
---

### Post by Rabid Fanboy on 2009-10-25
I'm setting up a computer by a TV, and the only way the monitor will fit is if I turn it sideways. After it was all set up, I was looking for ways to change the screen orientation. Apparently, it's not as easy  as "Ctrl+Alt+ArrowKey" =p

The first thing i tried was xrandr, but any command I entered either ended up as an error message or disappearing right when I press enter. Sorry for not giving you an example, today, everything I type in xrandr dissapears when I press enter =\
Then I tried getting a graphical interface for xrandr, but since xubuntu wont let me install things either, I couldn't do that. >.>
Today, I read about the xorg.conf file that I could edit. I believe I found it ( /usr/X11R6/bin/X11 ) but I can't do anything with it.

if it helps at all, I have a Samsung SyncMaster 715v monitor, resolution is 1152x864.

Thank you for your time. =]

---

### Post by Rabid Fanboy on 2009-10-25
sorry to have to double post in order to "bump" the topic, but I'd really like to get this figured out, I've tried a lot of things and still no results. =c

---

### Post by jmszr on 2009-10-25
Rabid Fanboy, 

This may be of help: [http://ubuntuforums.org/showthread.php?t=148177](http://ubuntuforums.org/showthread.php?t=148177)

---

### Post by Rabid Fanboy on 2009-10-25
-post is now obsolete-

---

### Post by Rabid Fanboy on 2009-10-26
I've opened xorg.conf, entered this into the device area

Option "RandRRotation" "true"

restarted, typed in "xrandr -o right" into the terminal
and I still have the error message, which is

X Error of failed request: 152 (RANDR)
Major opcode of failed request: 2 (RRSetScreenConfig)
Minor opcode of failed request: 12
Current serial number in output stream: 12

what do I do?

---

