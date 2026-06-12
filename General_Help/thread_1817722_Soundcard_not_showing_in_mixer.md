---
title: "Soundcard not showing in mixer"
date: 2011-08-03
forum: General Help
---

### Post by newlinux02 on 2011-08-03
Just installed ubuntu 11.04 but no sound. Turned volume on max for all controls and tried installing different packages.

When I put:

```
gnome-alsamixer
```

it brings up the mixer, but nothing shows. When I click "Soundcard preference" it closed and terminal shows:

```
(gnome-alsamixer:2598): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```

Nothing is showing up in "Input Devices" in pulseaudio volume control either, and for "Output Devices" it only shows "Dummy output"

Basically my sound is messed up here. No sound.

I think that I'm missing something that is supposed to be installed here. Any suggestions on what to install or re-install, or how to fix this?

---

### Post by newlinux02 on 2011-08-03
Could this be fixed by installing the gstream packages? Do they have anything to do with it?

UPDATE: I fixed it. I had my onboard audio off in my bios settings. Turning on the onboard audio through BIOS fixed the problem.

---

