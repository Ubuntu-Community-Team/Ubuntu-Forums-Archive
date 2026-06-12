---
title: "Set fan speed with Gallium drivers"
date: 2012-03-15
forum: General Help
---

### Post by ayozito on 2012-03-15
Hi!

I have an ATI HD 5770 but I'm using the free drivers Gallium because with the ones of ATI I have crashes using Gnome Shell.

Using ATI drivers I can set the fan speed with "aticonfig --pplib-cmd "set fanspeed 0 %""  but since I'm not using them, I can't use the command aticonfig...

So.. how can I set a constant % using Gallium drivers? Actually I guess that the fan is running at 50% or more... too loud for be practically on idle.

---

### Post by 2F4U on 2012-03-15
Thats not the way the open source drivers are working. Instead of setting a constant % you set either a profile or tell the driver to dynamically manage frequencies. As a warning, in my experience, dynamically changing frequencies leads to screen flicker at the moment the frequency changes. Here is some more information on what options are available:

[http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options](http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options)

---

### Post by ayozito on 2012-03-15
How can I save that file? 

I tried as root but can't save the file. 

Using Vim it said something about failed fsync. Using Gedit it said that can't create a backup, that save under my own risk, but also it didn't let me save....


nvm I did it

---

