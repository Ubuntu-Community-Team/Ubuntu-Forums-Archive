---
title: "Running Karmic (Release) with kernel 2.6.30.x possible?"
date: 2009-11-02
forum: General Help
---

### Post by KampfCaspar on 2009-11-02
Hi!

During the release cycle, Karmic has been upgraded from kernel version 2.6.30 to 2.6.31. 

Unfortunately - for the time being - our little shop has no kernel coder at hand. As such, we are stuck with a module only working on 2.6.30.x.

Just grabbing the debs from the ubuntu kernel PPA, I can install e.g. 2.6.30.9. It does boot an works, but /dev (udev? no subdirectories in /dev) and usb (/dev/bus/usb missing) does not seem right.

A little googling only explains incompatibilities with kernel versions much older than 2.6.30 (signalfd).

I was wondering if there is any chance running Karmic (Release) on 2.6.30? It was in the cycle, at least...

KampfCaspar

---

### Post by krantix on 2009-11-02
that would also help people who cannot load a custom dsdt anymore (my gpu is overheating since 2.6.31 as I cannot fix toshiba's buggy bios).

---

