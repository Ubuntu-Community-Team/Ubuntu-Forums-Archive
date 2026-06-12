---
title: "Ubuntu 11.10 CRASHES with very big pictures"
date: 2012-01-31
forum: General Help
---

### Post by fmmarzoa on 2012-01-31
Hi there,

I am facing problems on my VAIO with very big pictures taken from shutterstock.com. 

When I open them with the default image viewer that comes up when you double click in the picture within a Nautilus window, and move through the pictures on folder using left and right arrows, it crashes randomly at some of the pictures, but not only the viewer and nautilus dies, it crashes the whole X Window session bringing me to the login screen.

On another Acer laptop I own, I have not experienced such problems. This one has an nVidia graphic card, while the VAIO has an ATI RADEON, and I think its driver may be the most probably source of the problem.

Anyway, from where should I start to debug this in order to identify the source of the problem and solve it or fullfill a BUG report?

Regards,

---

### Post by fmmarzoa on 2012-02-01
I managed to solve it just setting Shotwell as default application for opening JPEG images instead of default gnome image viewer.

Regards,

---

