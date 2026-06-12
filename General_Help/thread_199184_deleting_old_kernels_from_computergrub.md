---
title: "deleting old kernels from computer/grub"
date: 2006-06-18
forum: General Help
---

### Post by axle_foley00 on 2006-06-18
Hello everyone,

I noticed that everytime a new kernel comes out it adds it to the grub list of kernels/OS'es. This list has grown rather long for me and I was wondering are those older kernels still necessary? If not then what is the best way to delete them and leave only the most recent? And finally I normally let my default boot OS be Windows XP, is there a way to let it always choose that OS even after a new kernel is added without me having to go into /boot/grub/menu.lst and change the default value?

:D

---

### Post by DarthMandeep on 2006-06-18
You could use Synaptic to uninstall the old kernels, if you never boot them they're of no use.

---

### Post by syxbit on 2006-06-18
in synaptic manager do a search for
"linux-image"
the ones with a green box are installed.
just make sure you uninstall the ones you're not running (i've never tried uninstalling the kernel running, but i assume it wouldn't work)

---

### Post by eth on 2006-06-18
if you don't want to loose those kernel (maybe tweaked and recompiled) but you wish not to see them at every boot just comment the proper menu.lst lines (#)

---

### Post by axle_foley00 on 2006-06-18
Thanks guys. I haven't tweaked any of the kernels and I haven't needed to go back to any of the old ones so I will try using Synaptic to uinstall them.

Thanks so much for your help. It's much appreciated.

---

