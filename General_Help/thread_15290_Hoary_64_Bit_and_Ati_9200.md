---
title: "Hoary 64 Bit and Ati 9200 ?"
date: 2005-02-13
forum: General Help
---

### Post by boardercrime on 2005-02-13
Hi 

I try to install a ATI 9200 on the Ubuntu 64 Hoary, but no luck.
Tried first with apt-get install xorg-driver-fglrx and then with the driver from ati.com.
After a modprobe fglrx this error appears:

FATAL: Error inserting fglrx (/lib/modules/2.6.10-3-amd64-generic/kernel/drivers/video/fglrx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and dmesg:
fglrx: Unknown symbol pci_map_single
fglrx: Unknown symbol pci_unmap_single
fglrx: Unknown symbol remap_page_range
fglrx: Unknown symbol pci_find_class


 ](*,) 

What's wrong ?

---

### Post by boardercrime on 2005-02-15
C'mon, nobody a clue ? If the nvidia works fine under Ubuntu 64 i will get one, who got's 3d Opengl working under Ubuntu 64 Hoary ???

---

### Post by tkw on 2005-02-23
Hi Boardercrime.

I have AMD Atholon 64 3000+ and  I'm just myself hesitating between:

A) Get the fglrx drivers for my Warty, compile kernel (the config needs finetuning, I understand) and then compile the fglrx kernel driver... Not very attractive, since this will lead me to continuous kernel compiling, when I update to newer kernels.

B) Upgrade Warty to Hoary and try get everything working just by a few clicks in Synaptic. Seems to be a hard route, too, when looking at your experience.

Just out of curiosity:
Did you upgrade Warty to Hoary or did you install Hoary dev release from scratch?

Then, just a guess: maybe you can find the root cause for your problem from the kernel configs. Have you checked your kernel configuration? It should match the requirements listed on 

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

The hint at the anchor point:

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#modversions-problems](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#modversions-problems)

lead me think you might have some kernel config problems, too.

BR, TKW

---

