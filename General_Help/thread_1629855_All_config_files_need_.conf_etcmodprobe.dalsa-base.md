---
title: "All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1?"
date: 2010-11-24
forum: General Help
---

### Post by a quarter past seven on 2010-11-24
this came up when i booted up and the disks were being checked, and its just come up again now

when i typed in **'sudo modprobe kvm'**

then this appeared below

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1, it will be ignored in a future release.


how do i get the modprobe thing?

---

### Post by a quarter past seven on 2010-11-27
bump

---

### Post by coabiguy on 2011-02-26
WTF does dump mean?

---

### Post by coabiguy on 2011-02-26
I am getting the same messages while booting.
My output from sudo modprobe kvm is

modprobe kvm
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'modprobe'

How do I get rid of this problem>

---

