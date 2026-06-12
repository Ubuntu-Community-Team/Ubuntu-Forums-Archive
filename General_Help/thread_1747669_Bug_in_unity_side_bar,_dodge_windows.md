---
title: "Bug in unity side bar, dodge windows"
date: 2011-05-02
forum: General Help
---

### Post by ceposta on 2011-05-02
The unity sidebar is supposed to dodge windows according to the default, and according to the settings in the unity prefs in compiz. This is not the case, as can be seen in this screenshot. Any idea what this could be caused by? It's sporadic when it shows up, but when it happens it does it until I reboot.

---

### Post by roboa1983 on 2011-06-01
ceposta, 
Have you figured out how to fix this? 
I've been having the same problem for the last couple of days. I tried to change things on ccsm, but to no avail.

---

### Post by ceposta on 2011-06-02
It has something to do with running java programs (under the Sun JDK, and possibly even the OpenJDK... couldn't pin it down exactly). When it happens, I look in the system log and I see errors about the unity-window-decorator crashing. When it happens, I can usually get it back with unity-window-decorator --replace from the command line. HTH

---

### Post by roboa1983 on 2011-06-02
ceposta,
Thanks! I'll keep my eyes open to see what happens when I run java-based programs. Incidentally, yesterday I was running one such program.
These morning I looked at the computer again, and the bar seems to be behaving normally, even though that java program is still running...
I'll try the command you mention once this happens again.

---

### Post by ceposta on 2011-06-02
yah, it never seemed to be very deterministic for me... just kinda random... whenever there seemed to be an internal JVM error or something... it's weird.. hopefully they come up with a Sun JDK package we can get that's supposed to work properly with Ubuntu 11.04. good luck!

---

