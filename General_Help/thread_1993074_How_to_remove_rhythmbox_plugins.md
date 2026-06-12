---
title: "How to remove rhythmbox plugins"
date: 2012-06-01
forum: General Help
---

### Post by samwillc on 2012-06-01
Hi everyone,

I thought I'd try rhythmarty to browse my music covers as it would make it more like the excellent musicbee on windows (I miss that player!!).

However, after I downloaded and installed the 64-bit rhythmarty deb file, it doesn't show up in the plugins list, nor as installed in the software centre. It is however here:

usr/lib/rhythmbox/plugins/rhythmarty

How can I remove this via the terminal as I can't do it via software centre? Or is it just a case of deleting that folder?

I'm using rhythmbox version 2.96.

Thanks in advance for any input.

Sam.

---

### Post by Frogs Hair on 2012-06-01
You can remove it from the synaptic package manager if installed or from the terminal .```
sudo apt-get remove rhythmarty
``` I see the package at Gnome Look hasn't been updated since 2010 and that may be the problem.

---

### Post by samwillc on 2012-06-01
> **Frogs Hair said:**
> You can remove it from the synaptic package manager if installed or from the terminal .```
sudo apt-get remove rhythmarty
``` I see the package at Gnome Look hasn't been updated since 2010 and that may be the problem.

Brilliant! Thanks.

Installed banshee instead as that has artwork and that's a must have for me.

Sam.

---

