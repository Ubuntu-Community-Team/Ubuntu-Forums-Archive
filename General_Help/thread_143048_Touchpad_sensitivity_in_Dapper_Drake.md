---
title: "Touchpad sensitivity in Dapper Drake"
date: 2006-03-11
forum: General Help
---

### Post by orn on 2006-03-11
I just update to Dapper Drake and my touchpad is very unsensitive, and doesn't respond to any changes, whether it be within the gnome mouse settings or by running xset manually.

Does anyone know what this could be?

---

### Post by Jott on 2006-03-19
Hi,

I had a similar problem with my hp zv5000 series with an alps touchpad.  I fixed it by copy a model configuration from the README in the driver files into the devices section of the xorg config file and then adjusting them a little, based on the response of the touchpad.  I forget what the paths to those files is, but if you do a forum search I'm sure you'll find it - matter of fact, you probably already have!

good luck!

---

