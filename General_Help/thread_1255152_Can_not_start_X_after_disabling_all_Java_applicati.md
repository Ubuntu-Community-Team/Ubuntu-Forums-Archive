---
title: "Can not start X after disabling all Java applications"
date: 2009-09-01
forum: General Help
---

### Post by JuJuBeans on 2009-09-01
Hi,

I could not make Java work on Firefox, so I was told to disable all Java on Synaptic. I unistalled all marked and then the screen went black, and could not get the ordinary boot.
I get the 

exec: 5: /usr/bin/X11/X: not found
xinit: Server error

message..

---

### Post by Mighty_Joe on 2009-09-01
> **JuJuBeans said:**
> . . . so I was told to disable all Java on Synaptic. 

Wow.  I'd scratch that person off your go-to-for-help list.  It sounds like you uninstalled Xwindows. Are you at a command prompt? Try running the command:
```
sudo apt-get install ubuntu-desktop
```
This should install the basic Ubuntu desktop and all its dependencies (including X).

---

