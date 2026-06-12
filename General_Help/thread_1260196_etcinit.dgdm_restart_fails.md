---
title: "/etc/init.d/gdm restart fails"
date: 2009-09-07
forum: General Help
---

### Post by skern03 on 2009-09-07
Hi Family - the command in the title of this thread should restart the desktop manager, which I used to test fixing the screen resolution. On two machines I have, it fails. Both drop out of the desktop manager and into a text screen. Both show identical messages, on starting cups and the other starting logging. But the desktop manager never restarts and the only cure is Ctrl+alt+del.

Note: the actual command line from a terminal is, of course:

> sudo /etc/init.d/gdm restart

Machine 1: Desktop, running 2.24.1 (Ubuntu 2008-10-24); graphics card is an ATI 9200 Pro. It works flawlessly. Triple boot: Win XP, Ubuntu 8.1, Ubuntu 9.4.

Machine 2: Dell Inspiron 8600, running the same distro as above; graphics card is GeForce FX Go6200. This one had the proprietary NVidia driver installed, which I removed because it kept puking. Dual boot: Win XP, Ubuntu 8.1.

Any ideas why the restart command fails?

---

### Post by bumanie on 2009-09-07
I think it should be > sudo /etc/init.d/gdm start

---

### Post by tiagosales on 2009-09-07
No restart X in a gnome session, Try Ctrl + Alt + F1, log in shell and 
```
sudo /etc/init.d/gdm restart
```
Come back to X in Ctrl + Alt + F7 to F12.

You can use right alt + printscreen + k or Logout, for restart X.

Sales, Tiago.

---

### Post by skern03 on 2009-09-07
> **bumanie said:**
> I think it should be sudo 

Yes, I'm using sudo - just didn't put it my post. Thanks for pointing that out - I'll go fix it now.

---

### Post by skern03 on 2009-09-07
> **tiagosales said:**
> No restart X in a gnome session, Try Ctrl + Alt + F1, log in shell and 
```
sudo /etc/init.d/gdm restart
```


Logging out and back in on the laptop with the issue that prompted this thread never worked; had to reboot. 

However, what did work was your suggestion to log in when gdm shelled out of gnome, using Ctrl+Alt+F1. After that, I issued the restart command (although I think start would work just as well). I then got a login prompt, and was back in business.

Thanks for the solution!

---

### Post by tiagosales on 2009-09-07
You're welcome. ;)

---

