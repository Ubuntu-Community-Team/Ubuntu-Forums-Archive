---
title: "Vpython"
date: 2010-01-21
forum: General Help
---

### Post by Captain_Falafel on 2010-01-21
Does anyone know how to get vpython working under Ubuntu 9.10?
I've got IDLE (using python-2.6) installed as my python shell window, but I can't seem to get visual python working.
I know that there's a package in the repositories - visual python, which I've installed, but I can't seem to run it somehow. I've gone to their site with no luck on installation. 

Does anyone know anything that could help? Thanks in advance :)

---

### Post by kchen45 on 2010-01-22
Bump

---

### Post by marcusesses on 2010-01-30
I'll bump this thread as well.

Just installed vpython on 9.10. 

When I try to run the simple code

```
from visual import *
sphere()

```
using IDLE, nothing happens. When I try to run the code using the command
```
python filename.py
```
I get the error
```
Segmentation Fault
```
With no other information.

---

### Post by marcusesses on 2010-01-30
OK, the issue seems to be fixed by including the software source available [here]("https://launchpad.net/~ajmitch/+archive/ppa").

However, you can't interact with the visualization window with the mouse. I'll try to sort this out tomorrow, but I think the initial issue might be taken care of.

---

### Post by Captain_Falafel on 2010-01-30
> **marcusesses said:**
> OK, the issue seems to be fixed by including the software source available [here]("https://launchpad.net/~ajmitch/+archive/ppa").

However, you can't interact with the visualization window with the mouse. I'll try to sort this out tomorrow, but I think the initial issue might be taken care of.

I've added the software sources, but which packages do I install?
My problem usually occurs when I want to run a python script like this one for testing:
```
from visual import *
sphere()
```
All of a sudden, both my script manager and the python shell crash

---

### Post by Gawains Green Knight on 2010-01-31
Bump

I also updated the sources. Removed and re-installed python-visual. Nothing new.

---

### Post by Captain_Falafel on 2010-01-31
> **Gawains Green Knight said:**
> Bump

I also updated the sources. Removed and re-installed python-visual. Nothing new.

What's your problem.. is the python shell and vpython crashing when you try to run a test script?

---

### Post by Gawains Green Knight on 2010-02-01
I saved

from visual import *
sphere()

to a file named test.py and then ran

python test.py

to only receive a segmentation fault.

Never used python before so I may be doing something stupid....

---

### Post by Gawains Green Knight on 2010-02-03
Anyone had any luck with this yet?

Edit: Above fix seems to have worked on my xubuntu 9.04 (I'll have to see why it didn't work on my 10.04 at home), but now I'm seeing...

> 
python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from visual import *
>>> sphere()

(<unknown>:8194): GdkGLExt-WARNING **: Cannot open \xa0\u001f\xc2\u0008L.so

(<unknown>:8194): GdkGLExt-WARNING **: Cannot open \xa0\u001f\xc2\u0008L.so

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: Unable to get extension function: glTexImage3D even though the extension is advertised.

aborting...
Aborted

....getting there!

Edit:Edit:

sudo apt-get install libgtkglextmm-x11-1.2-dev

seems to fix it, but the window is a little messed up (no boundary or anything). But it works! Thanks!

Edit:Edit: Edit: Didn't work on Ubuntu 10.04

---

### Post by marcusesses on 2010-02-13
Re: the fix above. 

For me, adding the source lists I mentioned in my previous post, then running
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
``` 

Allowed me to run a vpython script and have it produce the desired result. 

I am unable to rotate or manipulate the figure produced with the mouse cursor, so perhaps an additional package that allows 3-d visualization (e.g. OpenGL) needs to be installed?

I haven't really looked into the issue since my last post, so maybe I will do that in the next couple days.

---

### Post by Captain_Falafel on 2010-02-14
> **Gawains Green Knight said:**
> Anyone had any luck with this yet?

Edit: Above fix seems to have worked on my xubuntu 9.04 (I'll have to see why it didn't work on my 10.04 at home), but now I'm seeing...

....getting there!

Edit:Edit:

sudo apt-get install libgtkglextmm-x11-1.2-dev

seems to fix it, but the window is a little messed up (no boundary or anything). But it works! Thanks!

Edit:Edit: Edit: Didn't work on Ubuntu 10.04

I installed that package it it works fine for me, but if I exit out of the window where vpython drew my figure (e.g sphere), it exists (or crashes) out of the other two screens: thepython shell and python text editor.

Other than that, all is well for me, I can handle having to reopen IDLE everytime, but it'll get kinda annoying.

---

### Post by Jaime E. Villate on 2010-03-01
Your problem is due to a bug in Idle: it should not be called with the option -n to avoid that it exits when you close the Vpython window. To fix that problem, edit the file /usr/share/applications/idle-python2.6.desktop
(for instance, sudo nano /usr/share/applications/idle-python2.6.desktop)
and remove the option -n in the line that reads:
Exec=/usr/bin/idle-python2.6 -n

---

### Post by Captain_Falafel on 2010-03-01
> **Jaime E. Villate said:**
> Your problem is due to a bug in Idle: it should not be called with the option -n to avoid that it exits when you close the Vpython window. To fix that problem, edit the file /usr/share/applications/idle-python2.6.desktop
(for instance, sudo nano /usr/share/applications/idle-python2.6.desktop)
and remove the option -n in the line that reads:
Exec=/usr/bin/idle-python2.6 -n

Thanks!! that did it :)

---

### Post by meng1usa on 2010-06-24
This is a great post.
it solved my problem. vpython on 10.04. Thanks for all the great responses.

---

### Post by zaenal on 2010-06-25
> **Gawains Green Knight said:**
> Anyone had any luck with this yet?

Edit: Above fix seems to have worked on my xubuntu 9.04 (I'll have to see why it didn't work on my 10.04 at home), but now I'm seeing...

....getting there!

Edit:Edit:

sudo apt-get install libgtkglextmm-x11-1.2-dev

seems to fix it, but the window is a little messed up (no boundary or anything). But it works! Thanks!

Edit:Edit: Edit: Didn't work on Ubuntu 10.04

Thanks, it works for me on Ubuntu 9.10.
For window boundary problem, disabling the Visual Effects of Desktop Environment could fix it.

---

