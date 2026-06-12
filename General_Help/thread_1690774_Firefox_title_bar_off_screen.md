---
title: "Firefox title bar off screen??"
date: 2011-02-18
forum: General Help
---

### Post by PerfectReign on 2011-02-18
I just recently installed 10.1 on a new system.  I'm going to use it basically for development since the kernel bug affects my other systems, still using 9.1.

when I loaded firefox - 3.6.x - i noticed the title bar is missing. It appears to be somehow over the top menu bar. (How did that get up there? I usually had it on the bottom.)

I looked and found [http://ubuntuforums.org/showthread.php?t=969885](http://ubuntuforums.org/showthread.php?t=969885) one thread that mentioned this.  However, pushing F11 and back does nothing. The menu simply stays at the top. 

In fact, I can't even expand it.

What's with the goofy colors, too?

---

### Post by williamts99 on 2011-02-18
Hold the Alt key down, then click and drag the window.

---

### Post by Habitual on 2011-02-19
run
```
metacity --replace
```

---

### Post by PerfectReign on 2011-02-19
Okay, that worked...


...for a minute.

Once I exited (by pressing CTRL+C) and exited teh terminal, I lost both the minimize/maximize buttons and any ability to type.



This is bizarre!

---

### Post by Habitual on 2011-02-19
alt+f2 *then *metacity --replace

---

### Post by PerfectReign on 2011-02-19
Okay, that worked. 

On reboot I had the correct window controls.


Thanks!

---

### Post by PerfectReign on 2011-02-19
So, why did this happen?

Also, would there be a way to get it working without having to downgrade to the command line and running some arcane command?

---

### Post by Habitual on 2011-02-19
kai:

I don't know, I just had an issue like this before.
I wound up *changing themes*

Try that. :)

---

### Post by WorMzy on 2011-02-19
> **PerfectReign said:**
> So, why did this happen?

Also, would there be a way to get it working without having to downgrade to the command line and running some arcane command?

Your window manager/decorator (metacity by default) was either closed by you, or crashed. Running the metacity command made the process restart. When you did this in a terminal, and then *closed* the terminal (presumably ignoring the "process running" warning), the process ended again, leaving you in the same situation you were in prior to running the command. Using the run dialogue (Alt+F2), made the process run in the background, unattached to any terminal. Restarting your PC made the process run anew, as it is, like the panels and nautilus, part of the GNOME environment (by default).

---

### Post by PerfectReign on 2011-02-20
OIC

You kind of scared me for a second. When I read "metacity" - not having a clue about it - I thought of "metasploit."

[http://www.metasploit.com/](http://www.metasploit.com/)

---

