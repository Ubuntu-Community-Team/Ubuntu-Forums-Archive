---
title: "General Help"
date: 2012-04-27
forum: General Help
---

### Post by lisati on 2012-04-27
> **louiel555 said:**
> How can i redeuce the size of the window while using different application

We're not sure what you mean. Are you talking about making a "window" on the display smaller, or are you talking about making room on your disk?

---

### Post by matt_symes on 2012-04-27
Hi

Take a look at 

```
wmctrl
```
to resize a window from the command line.

Something along the lines of
```

wmctrl -r "window name" -e 0, XPos, YPos, Width, Height
```Read the man page for wmctrl

```
man wmctrl
```and check out the <MVARG> argument. 

Kind regards

---

