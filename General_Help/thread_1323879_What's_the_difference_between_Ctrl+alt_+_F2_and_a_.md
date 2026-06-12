---
title: "What's the difference between Ctrl+alt + F2 and a normal Konsole?"
date: 2009-11-12
forum: General Help
---

### Post by mahela007 on 2009-11-12
What's the difference between the konsoles you can get by pressing Ctrl+Alt and F2 through F6 and a normal konsole windows opened in the graphical environment?

---

### Post by megamania on 2009-11-12
> **mahela007 said:**
> What's the difference between the konsoles you can get by pressing Ctrl+Alt and F2 through F6 and a normal konsole windows opened in the graphical environment?
The terminals you access with ctrl+alt+Fx are not dependant on the GDM (gnome or kde or...). In other words, if you use some program on terminal 1, you can start/stop gnome or kde without affecting that program.

In fact, and put in simple words, gnome/kde and the other graphical environments are programs launched from terminal 7 (ctr+alt+f7)...

---

### Post by mahela007 on 2009-11-12
wow.. never though it might be like that..!
So then, what does the normal konsole window opened up in the desktop connect to? BTW.. what's GDM?

---

### Post by megamania on 2009-11-12
> **mahela007 said:**
> wow.. never though it might be like that..!
So then, what does the normal konsole window opened up in the desktop connect to? BTW.. what's GDM?
the "normal" console is a terminal which is nested into the graphical environment you're running.

Regarding GDM, it's Gnome Display Manager. My reply was quick so it wasn't very precise. There's actually a lot to say, and you may want to google for things like "linux x" or "linux graphical environment" to find out more.

Anyway, when you use a graphical environment, you're actually using (1) X, or Xorg, which is a graphics manager, and on top of it (2) a window manager (like IceWM) or a complete Desktop Environment (DE) like gnome or kde.

As I said, google will give you lots of explanations (for sure more accurate than mine) on this.  :-)

---

### Post by mahela007 on 2009-11-12
what does nested mean in this context?
does it mean something like "terminal within a terminal"? That's just a wild guess because I know about "nested" if statements in python

PS
I've been reading a bit of those topics (X an window managers) on google.. and I use the forums for confirmation.
Actually, the I didn't find an answer to the question I posted anywhere else. Thanks for helping.

---

### Post by megamania on 2009-11-12
> **mahela007 said:**
> what does nested mean in this context?
does it mean something like "terminal within a terminal"? That's just a wild guess because I know about "nested" if statements in python

Yes, I meant that it is a terminal which is launched from within the graphical environment. If you stop the GE, the process in the terminal will be stopped too (unless you detach it, but that's a different story...).

> **mahela007 said:**
> 
PS
I've been reading a bit of those topics (X an window managers) on google.. and I use the forums for confirmation.
Actually, the I didn't find an answer to the question I posted anywhere else.

I haven't checked, but I'm sure there must be something on wikipedia, for example.

> **mahela007 said:**
> 
 Thanks for helping.
You're welcome. I'm not a master, so take my words with a bit of caution.  :-)

---

### Post by mahela007 on 2009-11-12
> **megamania said:**
> 


I haven't checked, but I'm sure there must be something on wikipedia, for example.

 " I meant I didn't find it anywhere else... but I found it here".. i.e on this thread.
thanks again.. Marking thread as solved..

---

