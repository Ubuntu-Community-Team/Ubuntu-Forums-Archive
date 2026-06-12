---
title: "Multiple CPU Core Utilization"
date: 2009-07-06
forum: General Help
---

### Post by jumbofishmeat on 2009-07-06
Is there any known way to utilize multiple CPU cores by single processes in Ubuntu 9.04?

---

### Post by Arup on 2009-07-06
Ubuntu and Linux in general ultilizes all the cores far more efficiently than Windows. When I compile, I see all my eight cores in full action, there are certain programs though that like to hog one core at a time but I have seen Ubuntu shifting cores for those. In general most of the installed programs are either multi core aware or have provision to be made aware like WinFF which has an option to enable multi cores. Programs like Avidemux, Handbrake etc. use all the cores by default, Gimp detects your core and uses them by default as well.

---

