---
title: "Compiz acting up. Any suggestions."
date: 2010-12-28
forum: General Help
---

### Post by valhemmer on 2010-12-28
I've had this problem with compiz where it doesn't start on boot. I have to open a terminal and run compiz, then alt-f2 run it again to keep it going. I know thats not the best way to get it to run  but it works. this is the error i get when i run it in a terminal.

WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
inotify_add_watch: No such file or directory
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

I've searched for this error on google and I've found a couple of old bug reports that seem to have never been resolved. I've also tried reinstalling compiz with no effect. I was wondering if anyone else has had something like this and if anyone has a recommendation.

Because compiz doesn't run on start up docky/conky and window borders(max/min/close buttons) dont work properly. I basically have to spend about 30sec on the command line every time i boot. It doesnt bother me too much but it affects the other users of this computer.

Thanks all and happy holidays.

---

### Post by Janiporo on 2011-03-29
I have exactly same thing.

My compiz worked for long time with meny effects.
Originally I installed compiz-effects when I had just one monitor, now I have two, and first time I changed settings with two monitors, and restarted computer, almost nothing works.

Have you had any solutions to "reset" compiz?

So when I start computer I type "compiz" at the terminal (just like you), and get these normal borders around windows, etc. But still I have NO desktop effects running, even they are set to be on (compiz setting manager installed and works, but does nothing)

---

### Post by realzippy on 2011-03-29
As a valid workaround for "not starting" compiz put
```
compiz --replace
```
in System/Settings/StartupApplications

For "not working compiz" with 2 monitors there might be different reasons
- graphicscard/driver not capable of
- not configured driver

If [you give more informations]("http://ubuntuforums.org/showthread.php?t=1422475") about your system and setup,maybe someone can help you.

---

