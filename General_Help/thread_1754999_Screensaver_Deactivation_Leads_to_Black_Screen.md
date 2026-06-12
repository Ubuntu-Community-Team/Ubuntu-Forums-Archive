---
title: "Screensaver Deactivation Leads to Black Screen?"
date: 2011-05-10
forum: General Help
---

### Post by Githlar on 2011-05-10
I get this very occasionally, but in the 3 days I've had my computer powered up for this session, it's happened three times.

Problem: After moving the mouse to deactivate the screensaver, the Locked screen appears. Then, after typing the password and pressing enter, the Lock screen disappears, leaving the whole screen black with just a cursor. Nothing ever appears. When you move the mouse around, you can see that it changes depending on what *would* be under the mouse (i.e. a text field), but it's still all black.

The only solution I've found to this is Ctrl+Alt+F1 and then `sudo restart gdm`

I haven't tried to wait it out for the screensaver to re-activate to see if the problem persists. I have, however tried a blind Alt+F2 `gnome-screensaver-command -a` which didn't seem to work.

I have tried: closing the laptop lid (too see if a sleep/wake would make it responsive again) - that didn't work.

This is a very annoying problem. It's not frequent, but frequent enough to cause problems. I mean, I do a lot of crazy stuff on my computer and at an given time I probably have at least 10 windows open. So, having this happen and not having a remedy means that I lose any currently running scripts, programs, etc when GDM gets killed.

Here's my relevant setup:
Ubuntu 11.04 (Unity-enabled)(i386 2.6.38-8-generic-pae)
Intel GM965 graphics (8M shared and horribly incapable, but it can still run Unity? I'm not complaining =P)
Blank screensaver

As of yet, I haven't been able to determine any constant between the incidents, but I'll keep looking. In the mean time I'm going to run Unity out of a terminal (with stdout and stderr piped into a file) and when it happens again I'll see if I've got anything in a log. I'll also try waiting it out next time and let the screensaver re-activate.

---

### Post by TheNerdAL on 2011-05-10
This might not help, but how about instead of using the screensaver, just change the settings so that the monitor will turn off when idle. There are a lot of screensaver bugs for 11.04.

---

### Post by Githlar on 2011-05-11
I haven't had the problem again (yet). Still, something about the screensaver is the issue. I'm the type of person that I'd rather fix the problem than avoid the problem (if nothing else, it'll help somebody else out in the long run), so for the moment I'm going to see if I get any info logged for this error. I'll also try to avoid doing anything that I can't easily kill!

---

### Post by jflinux on 2011-05-11
It's a real bug that just appeared after up grading to 11.04 ubuntu.  My toshiba A205 laptop goes into screen saver and won't
ever come out of it.  I can see a blank screen with the mouse moving, but it never brings back my desktop, start menus, or browsers.   Have to hard power off or go to terminal mode by
typing <ctrl><alt><f1> , log in, shutdown -h 0.

Getting rid of screen saver and going directly to a suspend state did not fix it, but it seems to happen less often with that change.

I don't lock the screen with a password when doing screen saver.

---

### Post by ikhalil on 2011-05-21
I have exactly the same problem on a couple of machines after upgrading to 11.04
It happens at random intervals with no consistency.

---

