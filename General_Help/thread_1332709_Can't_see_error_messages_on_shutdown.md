---
title: "Can't see error messages on shutdown"
date: 2009-11-20
forum: General Help
---

### Post by danebramaged on 2009-11-20
Hello everybody:


I see error messages as I shutdown.  They go flashing by after the last "splash screen" so I can't see them.

I am guessing that they are in a log? file somewhere? So, if you guys could point me to where i might the error messages, i will post them here for all to see.

I am running 8.10.

I see what looks to be the same error messages (approx) at least every other time I shut down.  Sometimes back to back.

But it's like I said; it all goes by too fast so, this is just a generalization when I say the error messages look approx. the same.

The system seems to be working though.  It only gets used for music, email and surfing.  


please help and thanx.

:-k

---

### Post by P4man on 2009-11-20
have a look at 
/var/log/messages
But i wouldnt worry too much, its usually just warnings when shutting down and nothing to lose sleep over.

---

### Post by danebramaged on 2009-11-20
> **P4man said:**
> have a look at 
/var/log/messages
But i wouldnt worry too much, its usually just warnings when shutting down and nothing to lose sleep over.

it almost looks like the last line that flashes by is a directory.

I looked in the logs and the only thing i see is references to the wi-fi which looks nothing like what i get a glimpse of after the shutdown splash screen.

How do I turn off the splash screen and go verbose with the output.

Is there an option to pause or stop on error on the way down?

thanx

---

### Post by stonebit on 2009-11-20
Log out of ubu and goto a console - ctrl+alt+F1. 
Log onto the machine at the console.
Type this to reboot:
sudo shutdown -r now
or this to shutdown:
sudo shutdown now

This will show you everything output that is normally covered by the gui goop.

---

### Post by danebramaged on 2009-11-21
> **stonebit said:**
> Log out of ubu and goto a console - ctrl+alt+F1. 
Log onto the machine at the console.
Type this to reboot:
sudo shutdown -r now
or this to shutdown:
sudo shutdown now

This will show you everything output that is normally covered by the gui goop.

When I logout as per the above,  the same error messages are sitting there, waiting for me to glimpse, except for now they are visible  just before I actually get to the splash screen.

There is a reference to /etc/rc.local on the very last line and I think the number 14 was on that line but, I didn't catch the rest of it.

How do I boot up and shutdown ubuntu without any splash  screens getting in the way?

---

