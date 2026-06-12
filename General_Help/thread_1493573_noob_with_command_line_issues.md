---
title: "noob with command line issues"
date: 2010-05-26
forum: General Help
---

### Post by lanching123 on 2010-05-26
there is a particular command line i have to run to make my wireless card work (im using ndiswrapper).  how do i make it so that command line is preformed each and every start up automatically.  as it is now i have to enter this command every time i turn my computer on if i want to use my wifi card but i want it to work upon start up.  thanks for your help and patience.  oh im using ubuntu 10.04

---

### Post by lanching123 on 2010-05-26
SOLVED!  sorry i gave it one last try and got it.  sorry about that!  i told ya im a noob at all this

---

### Post by sdennie on 2010-05-26
It depends on how soon you need it to run.  Most likely, you can add it to /etc/rc.local.  In /etc/rc.local you will see an "exit 0".  Put your command above the "exit 0" (you may want to gksudo gedit /etc/rc.local to do that) and it will likely work because that file gets executed toward the end of the boot sequence.

---

### Post by stinger30au on 2010-05-26
what did u do to solve it?

---

### Post by inso_741 on 2010-05-26
maybe he used 'startup applications'?

---

### Post by jerome1232 on 2010-05-26
You just put "ndiswrapper" in /etc/modules.

---

