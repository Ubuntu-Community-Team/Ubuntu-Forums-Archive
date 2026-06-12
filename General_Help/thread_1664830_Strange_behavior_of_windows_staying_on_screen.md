---
title: "Strange behavior of windows staying on screen"
date: 2011-01-11
forum: General Help
---

### Post by hey_there_bro on 2011-01-11
So I have Ubuntu 10.10 64 bit, and I'm having strange problems with parts of windows staying up on screen after I close them. Check the attached files to see what I mean. I have Visual Effects turned off, and I've tried removing compiz altogether, but I still see this happen every once in a while. Any suggestions?

---

### Post by ajgreeny on 2011-01-11
What is your hardware, particularly your graphics card?  This looks like a graphics card driver problem to me; it's something I see occasionally with my old ATI 9200SE card with the open source radeon/ati driver, the only driver available now.

I do run compiz on the desktop very well, even with that card, and whenever I see that artifact on screen, I simply press the middle button of the mouse, which momentarily shows the compiz cube, and that strange part-window disappears.

Incidentally, I never get this happen over another window, only when I have an empty desktop showing;  is it the same for you?

---

### Post by hey_there_bro on 2011-01-11
Well it's a laptop, so I have an ATI x1270 I believe. I've installed a graphics driver named ati-driver-installer-9-3-x86.x86_64.run which after some searching, was found to be the driver for my graphics card. 

I don't know about the compiz cube because I have all that turned off. This happened even whenever I uninstalled compiz.

---

### Post by ajgreeny on 2011-01-12
Not sure about the ATI x1270, but ATI can cause problems in linux, though it's getting a lot better.  I still think this is the probable cause, but don't know how to solve it.

---

### Post by sum1nil on 2011-01-12
Not sure about this route, but what windowmanager are you using?

You can find it one way by opening a terminal and entering 'gconf-editor'.
Once the editor launchs browse to:
/desktop/gnome/session/required_components/windowmanager
or search for windowmanager using find to see what it says.

---

### Post by hey_there_bro on 2011-01-13
It says I'm using metacity.

---

