---
title: "ubuntu 9.04 &quot;freezes&quot;"
date: 2009-08-07
forum: General Help
---

### Post by tudor_victor on 2009-08-07
I have been running the previous stable Ubuntu release with no problems for about 6 months now.

two days ago I decided to upgrade to 9.04 using synaptic.

since then my computer has "frozen" twice.

my computer runs constantly. I leave some programs like firefox running all the time.
after several hours of inactivity I come back and the computer is ******.

the first time I had left sudoku running and the next morning I was unable to close it.
this time I left firefox running and when I came back my mouse scroll wheel was not working anymore, and when I tried to load a new page, firefox froze.

both these times, after the app crashed, the OS was still running (the other applications worked fine) but I was unable to execute any further operations. I can't run new applications. I can force quit the frozen app but no more applications can run, not even something like system monitor.
I can't even shut down the system from the graphical interface, I need to switch to a terminal and use "reboot now" to restart the PC.

Any ideas how to troubleshoot or fix this problem?

---

### Post by tudor_victor on 2009-08-08
it happened again that the mouse wheel stopped working but this time the OS wasn't frozen.

I noticed that my CPU was at 100% and Xorg and imwheel were taking up the whole processor.

apparently imwheel is causing resource problems with ubuntu 9.04

I uninstalled imwheel and installed btnx. hopefully this will solve the issue.

on the plus side btnx comes with a graphical configuration tool that autodetects the mouse so configuration is much easier.

---

### Post by nacho32 on 2009-08-08
personally I shy away from upgrading the os to one version to the other usually has problems, fresh install the best way to go

---

