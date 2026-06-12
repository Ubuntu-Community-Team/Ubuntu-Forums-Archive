---
title: "Does XGL/Compiz work in VMware?"
date: 2006-06-24
forum: General Help
---

### Post by fyleow on 2006-06-24
I've been trying to install XGL/Compiz on Ubuntu running on VMware but I'm having some issues.  I followed the instructions on the Wiki and I run into problems when I try to run Compiz.

When I try:

compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water &

I get the error:

compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display:1.0

I also lose all control of windows and have to reboot Ubuntu.

---

### Post by FredB on 2006-06-25
VMWare graphic video is not supporting 3D. So no glx / compiz support.

---

