---
title: "A package (libsdl related) requires me to remove the &quot;ubuntu-desktop&quot; package .."
date: 2011-06-04
forum: General Help
---

### Post by Milkman08 on 2011-06-04
I need to install the following packages in order to compile a [ScummVM]("http://scummvm.org") fork that is not already compiled for ubuntu.

libsdl1.2-dev
libsdl1.2debian-all

But installing via Synaptic requires me to remove the "ubuntu-desktop" package.

What should I do?

---

### Post by mc4man on 2011-06-04
> What should I do?You don't need to do anything, ubuntu-desktop is just a 'meta' package just has depends and  recommends
If you later decide to do an upgrade to a new ubuntu release then  best to re-install before doing so

(it's possible that you could re-install now if inclined - it may, (should) recognise that libsdl1.2debian-all provides libsdl1.2debian-pulseaudio which is a depend

---

