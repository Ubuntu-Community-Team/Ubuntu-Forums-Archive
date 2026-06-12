---
title: "Nvidia problems!"
date: 2006-01-21
forum: General Help
---

### Post by tappad on 2006-01-21
Hi.

I'm having some problems with NVIDIA drivers.
Lots of programs won't run eg. Mplayer, xmms + some others (Segmentation fault, something like that). I have discovered that it all works fine if i just reinstall nvidia package (with synaptic). However, as soon as my computer is rebooted the problem reappers, so i have to do this on every boot and it's getting frustrating.. Any ideas?

Also, if i enable glx (nvidia-glx-config enable).. X wont start at the next reboot.. So then i have to reload Xorg.conf, and everything will be ok..

Would really appreciate any help.. (And im sorry about any grammar/spelling)

Best regards!


ps. Also, im getting this "Warning from synaptic":
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by tappad on 2006-01-24
bump!

---

### Post by rjwood on 2006-01-24
you may want to comment (#) out your cdrom line in your /etc/apt/sources.list file. As for the nvidia drivers --- search 'nvidia' and see tseliot's 'how-to'. 

Incidentially---what version of ubuntu are you running (breezy--hoary or dapper)??

---

### Post by tappad on 2006-01-25
im using breezy..

I've tried the HOWTO, but cant seem to get it right..
I think it's strange that mplayer, xmms works when i reinstall nvidia-glx..
And then stops working after a reboot..

tnx

---

