---
title: "Ctrl+{Any alphabet letter} does not work in Java apps"
date: 2011-05-03
forum: General Help
---

### Post by alex_sv on 2011-05-03
I've Intellij Idea and Netbeans installed on my Ubuntu desktop. Both worked fine while I was on 10.10.
After upgrading to 11.04 both of them became irresponsive to Ctrl+C/Ctrl+V/Ctrl+{Any alphabet letter} combinations. However these combinations work in non-Java apps (e.g. gedit).

Besides that Ctrl+Alt+L (Lock screen) is not handled by the system, no matter what application is active.

Disabling unity does not help. Starting in ubuntu classic w/o effects does not help either.
Does anyone know how to deal with such a problem? :confused:

---

### Post by cipherboy_loc on 2011-05-03
What version of Java are you running?



Cipherboy

---

### Post by alex_sv on 2011-05-03
Looks like that I've found workaround:
(1) switch to 'Generic 105-key' keyboard layout
(2) remove any non-latin layouts (after reboot you can add it again) and leave only USA keyboard layout
(3) reboot

In addition I switched back to Ubuntu Classic without effects, but this step seems to be optional.

---

