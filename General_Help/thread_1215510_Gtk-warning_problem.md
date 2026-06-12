---
title: "Gtk-warning problem"
date: 2009-07-17
forum: General Help
---

### Post by taltas on 2009-07-17
Hello there,

I am trying to run Balsa, an asynchronous synthesis tool (NOT THE EMAIL CLIENT) on Ubuntu. While running the tool in super-user mode, I get the following error:

[I]Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
sh: emacs: not found[/I]

Please help, how do I solve this problem. Do I need some packages?

---

### Post by cwbar_1 on 2009-07-17
Go to Synaptic Package Manager and install from there.

---

### Post by taltas on 2009-07-17
> **cwbar_1 said:**
> Go to Synaptic Package Manager and install from there.

Install what from there?

---

### Post by cwbar_1 on 2009-07-17
Enter "libcanberra-gtk-module" (without the quotes) in the search box in Synaptic. The module will be found, and just click "Apply Changes" to install.  Re-boot and all should work.

---

### Post by taltas on 2009-07-18
I  already seem to have that package installed. I am thinking its a permissions thing, though I am already a superuser. Any ideas on what else it might be?

---

### Post by 3rdalbum on 2009-07-18
> **taltas said:**
> Hello there,

I am trying to run Balsa, an asynchronous synthesis tool (NOT THE EMAIL CLIENT) on Ubuntu. While running the tool in super-user mode, I get the following error:

[I]Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
sh: emacs: not found[/I]

I get this as well - I believe it's a false-alarm error message triggered when you try to run a 32-bit program on a 64-bit machine; it's looking for 32-bit libcanberra. Ignore it.

The real error message is "emacs: not found". You can install Emacs from Synaptic Package Manager.

---

