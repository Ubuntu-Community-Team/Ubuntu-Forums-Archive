---
title: "Update Manager says system is up to date - I'm pretty sure it isn't"
date: 2006-05-10
forum: General Help
---

### Post by nhwoods on 2006-05-10
I recently installed Breezy Badger 5.10 on a Compaq computer with a wireless network card and no ethernet port.  During installation, I got a message that said there was no network card installed, that it detected a firewire port (which I don't think my computer has), and that it was possible, though unlikely, that the firewire port could be used to connect to the internet.  It asked if I wanted to use this port for an internet connection, and I answered yes.

After installation, all is working OK, including the wireless card (after a little configuation difficulty).  The only problem is that when I run the update manager it says that my system is up to date.  I don't think it is as after I installed this same version on my other computer there were immediately many updates found and every week or so there are more.  The Compaq, however, remains up to date as far as the update manager is concerned.  I'm not sure if the initial problem with the network card during installation has anything to do with this or not.  I would appreciate any help I could get with this.

---

### Post by az on 2006-05-10
[QUOTE=nhwoods] I'm not sure if the initial problem with the network card during installation has anything to do with this or not.  I would appreciate any help I could get with this.[/QUOTE]

Using synaptic, can you see if you have not only the "breezy" main repositories, but "breezy-security" and "breezy-updates" main repositories enabled?   The same goes for any other repos (restricted, universe, multiverse)

---

