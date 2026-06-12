---
title: "Lucid - bunch of problems"
date: 2010-05-16
forum: General Help
---

### Post by 0026 on 2010-05-16
I installed Lucid Lynx on my Asus A3000, and found myself in a pile of problems.

First, as soon as boot screen shows, screen goes blank.
I figured out thats because i have i8xx chipset:

> 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I can still boot in safe mode, though.

After that i found out i can boot it normally if i switch to vesa driver.
So: /etc/X11/xorg.conf, but no xorg.conf anywhere. Only xorg.conf.failsafe, which i cant edit. And it already has graphics driver changed to vesa.

So i thought  "maybe there is no xorg.conf because of safe mod". I dropped to shell and tryied to change it there using "sudo dpkg-reconfigure xserver-xorg", but after i execute it, it only promprts me for a pass and nothing happens next.

I still cant load Lucid without going into "safe mode".


And guess what? I need help :)

---

### Post by oldfred on 2010-05-16
if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by 0026 on 2010-05-16
Nothing from there works for me, so i wanted to try a vesa driver out untill this issue is fixed.

But as you can see, i cant enable it anywhere.

EDIT: thx man. i915 modeset=1 worked out for me, in a way. It starts up normally but crashes to low-graphic mode after :(

---

