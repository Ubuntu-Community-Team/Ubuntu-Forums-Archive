---
title: "KVM / Multi-Computer Environment"
date: 2011-07-19
forum: General Help
---

### Post by evil_iggy on 2011-07-19
Hi All,

I've got a personal Dell desktop with an nvidia geforce 9400 GT with one vga and one dvi adapter and I dual boot windows and ubuntu. I've also got a work laptop issued to me by my employer that runs windows. I just bought a docking station for it and would like to set up my personal and work computers to use a monitor switch because it's a pain to disconnect and reconnect everything if I want to work remotely. 

Anyone have a suggestion for a KVM that works will with ubuntu?

Thanks in advance

---

### Post by jerrrys on 2011-07-19
can you run kvm? open a terminal and enter [B]kvm-ok

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=kvm&sa=Search&cof=FORID:9#881](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=kvm&sa=Search&cof=FORID:9#881)
[/B]

---

### Post by evil_iggy on 2011-07-21
good call on that, thanks.

INFO: Your CPU supports KVM extensions
INFO: /dev/kvm does not exist
HINT: sudo modprobe kvm_intel
KVM acceleration can NOT be used

---

### Post by evil_iggy on 2011-07-21
Looking for a 2 monitor setup. Reality is I can't do without that anymore.

---

### Post by matthew.mattoon on 2011-10-12
Hi evil_iggy,

Looks like the previous responder was confused on your issue.  Ubuntu contains Linux-KVM (Kernel-based Virtual Machine) which is a virtualization technology.

You are looking to have dual monitors or use some sort of physical KVM (keyboard-video-mouse) box.

With dual monitors usually you need to use jockey-gtk to install the nvidia or ati drivers for your video card, then use the control panel for the new driver to configure the video card as using multiple desktops.

With KVMs they usually just work, granted I have not seen any dual monitor KVMs, so that might be a pipe dream (or perhaps only monitor will "roll").

-matt

---

