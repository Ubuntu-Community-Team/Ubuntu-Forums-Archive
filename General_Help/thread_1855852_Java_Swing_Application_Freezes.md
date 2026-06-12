---
title: "Java Swing Application Freezes"
date: 2011-10-07
forum: General Help
---

### Post by Muhsin7 on 2011-10-07
Hi All

I am not sure if this is an Ubuntu or Java problem. My Java Swing Application that I wrote in NetBeans 7.0 sometimes freezes. The problem is that my background threads still run and only my GUI becomes unresponsive, to the point where I cannot even close it. I have to close it from System Monitor or stop it in NetBeans if I am debugging.

I cannot replicate the problem since it occurs on random ocasions and I am not sure what is causing it to freeze.:(

Regards
Muhsin Hoosen

---

### Post by veroslav on 2011-10-07
Are you doing any long running tasks on the EDT? That might explain why the EDT never gets the chance to repaint the GUI.
You could use SwingWorker and update the GUI from there, for instance.

Regards,
Veroslav

---

### Post by Muhsin7 on 2011-10-10
Thanks for the information Verosla.

Yes I do have some long running tasks, and according to the requirements this java application must be able to run 24/7.

I was away for the weekend and will work on getting the SwingWorker implemented into my software.


Regards
Muhsin Hoosen

---

