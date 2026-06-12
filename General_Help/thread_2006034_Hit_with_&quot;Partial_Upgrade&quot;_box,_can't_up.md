---
title: "Hit with &quot;Partial Upgrade&quot; box, can't update kernel"
date: 2012-06-18
forum: General Help
---

### Post by coldjeanz on 2012-06-18
Maybe about a week and a half ago I got the partial upgrade box when running updates through Update Manager. Been ignoring it for a while since it was only prohibiting me from updating some useless apps I no longer use. But now I can't update my kernel. See here

[IMG]http://i.imgur.com/FNl2Q.png[/IMG]

The checkboxes cannot be clicked on and I don't want to run the partial upgrade since I've heard some bad things about it.

I'm using Ubuntu 12.04, this happens on Gnome-Shell and Unity.

---

### Post by PhantomTurtle on 2012-06-18
The partial upgrade will update as many packages as it can and and try to fix whatever is wrong. It will update whatever it can so those apps you don't updated will still be updated if you do that. However this is probably the only way to update. If there is an app you don't want updated, remove it, run "sudo apt-get update" terminal and then open update manager and do the partial upgrade. It has worked for me before, but I can't guarantee it will work. If you let the partial upgrade go through then your updating problem should be resolved. It could be either doing that or never updating at all...

---

