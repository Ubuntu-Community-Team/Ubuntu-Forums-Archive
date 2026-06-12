---
title: "No screen"
date: 2010-10-08
forum: General Help
---

### Post by Jack0239 on 2010-10-08
Hello,  I installed ubuntu 10.4.  I am getting no screen on my display by HDMI. I installed after that the nvia driver but it won't work  800*600 by 60hz  My display works fine with Windows 7 on my other computer. I do my first steps with an open scoure OS so does Ubuntu support HDMI?

---

### Post by Tak11 on 2010-10-08
open a terminal, Applications->Accessories->Terminal

type > sudo nvidia-settings

hit X server display configuration, while the screen is attached.

enable the screen.

---

### Post by Jack0239 on 2010-10-08
Doesn't work at all.

---

### Post by Tak11 on 2010-10-08
you're going to have to be more specific, could you show me a screenshot of your nvidia-settings window?

---

### Post by Jack0239 on 2010-10-08
I typed in your command but nothing happened.

---

### Post by Tak11 on 2010-10-08
try this

hit alt + f2

type: gksu nvidia-settings

and then follow the rest of the instructions.

---

### Post by Jack0239 on 2010-10-08
Do you know how to get sound over HDMI:confused: I got a screen now - thank you very much indeed\\:D/

---

### Post by Tak11 on 2010-10-08
yes, click your speaker icon (top right corner) 
hit sound preferences
hit output
where you see 'Connector:' change it to the correct output (I'm not sure what that is, just play with it until you hear sound.)

---

### Post by Tak11 on 2010-10-08
if your problem is resolved you should prefix your thread with SOLVED: 
so other people who are experiencing a similar issue will know they can reference this thread.

---

### Post by Jack0239 on 2010-10-09
I tried all outputs but I can not hear a thing.

---

