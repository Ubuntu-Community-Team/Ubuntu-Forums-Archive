---
title: "Screensaver restarts X"
date: 2006-05-12
forum: General Help
---

### Post by 3str on 2006-05-12
My gnome restarts when the screensaver runs. Even if I run System->Preference->Change screensaver properties, the X restarts...
Why?

---

### Post by jasay on 2006-05-12
My guess (and that's all it it) is that your video card is not set up for 3-D acceleration and the openGL screensavers are causing it to crash.  The screensaver selection program shows a small version of the screensaver and so will crash since it needs 3-D acceleration too.  So, if I'm right, there are a few options.  #1 is the likely the best, but probably the most work.

1) Install drivers for you video card.  
If you want to do this, you'll need to know what kind of card you have.  If you don't know, there are ways of finding out.  Unfortunately I don't remember them right now.  This might be one of them: open a terminal (applications > accessories > terminal) and copy/paste the following ```
glxinfo | grep vendor
```Copy what it says into a new post here for more help.

2) Don't run a screensaver at all.
Open nautilus (applications > accessories > file browser) and hit control+h.  This will show hidden files.  Find and open .xscreensaver (note the period).  Scroll down a bit and should see a line that says```
mode:		random
```
change it to 
```
mode:		off
```Save the file and you're done.

3) Don't run a screensaver, just blank the screen.
Open nautilus (applications > accessories > file browser) and hit control+h.  This will show hidden files.  Find and open .xscreensaver (note the period).  Scroll down a bit and should see a line that says```
mode:		random
```
change it to 
```
mode:		blank
```Save the file and you're done.

4) Try to run  2-D screensavers only.
I think this will work.  Not as confident as the others.

Open nautilus (applications > accessories > file browser) and hit control+h.  This will show hidden files.  Find and open .xscreensaver (note the period). Scroll down a ways and it'll say "Programs:" followed by a long list of possible screensavers.  Keep scrolling until you find lines that start with a "GL".  These are the 3-D screensavers that are causing problems.  To stop them from running, put a dash, "-", in front of each line (yes there are a lot of them).  Save the file and you're done.

---

### Post by 3str on 2006-05-12
Thanks for that:)
I guess I should have OpenGL correctly. My video card is Nvidia FX5600. I've installed a driver for it months ago. I can play Warcraft III in cedega.
Anyway, I'll disable screensaver first.

---

### Post by 3str on 2006-05-12
Well, it is the video driver. I updated my kernel through apt-get. It seems the drivers needs recompile with the new kernel header files. I reinstalled it and everything turned fine.
Thx again:)

---

