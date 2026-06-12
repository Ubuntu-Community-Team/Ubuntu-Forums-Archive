---
title: "MP-bios bug"
date: 2009-10-23
forum: General Help
---

### Post by glenuk on 2009-10-23
since installing ubuntu 9.04 a while back i've been getting "MP-Bios bug:8254 timer not connected to IO-APIC" the only advice i've found is to add a line to the grub to say noapic but on doing that ubuntu refused to load & threw up a load of errors & i couldnt get into my desktop & as a result i had to reinstall ubuntu again is there any way to fix this without having to use the grub code 
thanks
glen

---

### Post by Meskarune on 2009-10-26
try noacpi instead and see if that works...

---

### Post by yoyoq on 2009-12-23
i tried all options and
i never could get a stable system with this bug.
workaround :

install 
the server edition, (i used 8.04)

then 
sudo apt-get install xserver-xorg-core gnome-core gdm ubuntu-gdm-themes xfonts-base synaptic

will get a baseline gnome desktop.
make sure you never install
anything with apic or anything that looks like it

---

