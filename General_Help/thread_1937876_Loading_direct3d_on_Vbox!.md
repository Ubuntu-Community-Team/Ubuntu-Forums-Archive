---
title: "Loading direct3d on Vbox!"
date: 2012-03-08
forum: General Help
---

### Post by Panxo on 2012-03-08
Hi there again. 

Last problem for now!

As some of you now, I'm using ubuntu 11.10 and Oracle Vbox 4.1.8 

The reason I want to load direct 3d is for playing games that I can't install on ubuntu like league of legends and honestly, I prefer to run Vbox rather than Wine. 

Well, last time I tried to load it have a lot of problems. Updating issues and starting sessions errors. The main cause of that is, I think, that OpenLG crashes with NVIDIA drivers. Fortunately, those problem are solved now.

What I did was: 

On win7 (guest): 

Install Directx 9.0c - Net 3.5 - Net 4.0 And no problem with that.

On ubuntu (host): I tried to install the NVIDIA drivers from both, terminal and synaptic, but it didn't work, just made things worse. Actually I did face some problems when trying to run Cairo-dock. 

Does any of you have another suggestion for loading direct3d on win7?

---

### Post by notone70 on 2012-03-08
You have to download VBGuestAdditions, burn it to a disk, goto devices and click on install guest additions. Then boot the win image up in safe mode and install it. This will give you a vbox video driver that will allow 3d rendering.

---

### Post by jerome1232 on 2012-03-08
It's a little bit easier to just load safe mode then press right ctrl+d to install the guest additions, you may need to go into my computer and double click the "cd drive" to get it going if it doesn't auto start

---

### Post by Panxo on 2012-03-09
Alright, I don't know what's happening, but... I run win 7 in safe mode, tried to install the guest additions, and nothing happens...

Tried to do it with the keyboard command, manually, and nothing shows up!

Does anyone know what's happening?

---

