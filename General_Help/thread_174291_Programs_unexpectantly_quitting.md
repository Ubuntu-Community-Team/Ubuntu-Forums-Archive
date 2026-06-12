---
title: "Programs unexpectantly quitting"
date: 2006-05-11
forum: General Help
---

### Post by mental_drummer on 2006-05-11
Hi,
Ive been noticing lately that programs keep closing without warning or an error message. D4x was doing it loads and i thought it was jsut that program but now firefox and gdesklets have started doing it too? Really weird. Has anyone got any ideas
p.s. ive only been running linux for about 2 months so go slow!
Niall

---

### Post by DJ Scribblinni on 2006-05-11
One awesome way to find some sort of error message is to open up the terminal.  Within that just type the program name that you would like to run.  Type "firefox", the program will open as normal, some stuff may or may not print out in the terminal.  When the program vanishes hopefully something was printed in there that will let you know.

Also within /var/log/ are various log files.  Check those out and see if you can't find anything in there.  Theres a handy Log Viewer, go to System>Administration>System Log.  Open up a log and snoop around.

---

