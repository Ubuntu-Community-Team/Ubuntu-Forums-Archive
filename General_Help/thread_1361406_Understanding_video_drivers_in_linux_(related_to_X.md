---
title: "Understanding video drivers in linux (related to X11)"
date: 2009-12-22
forum: General Help
---

### Post by mahela007 on 2009-12-22
I've read that drivers are the software that translate instructions in a program so that the instructions can be used by hardware. Now, how do video drivers work in a linux system with the X window system? 
The client programs tell X that they need to display certain graphics on a screen. What does X do after this? Does it hand those requests over to the kernel (which will then use the drivers to create the graphics) or does it directly use the drivers (without going through the kernel) in order to draw images on the screen?

---

