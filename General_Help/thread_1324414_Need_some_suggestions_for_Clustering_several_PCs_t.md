---
title: "Need some suggestions for Clustering several PCs together (Beowulf cluster)"
date: 2009-11-12
forum: General Help
---

### Post by BooDaddy on 2009-11-12
Hello all,
I have been thinking about setting up a Beowulf cluster, and I am needing some suggestions.

Heres what I would like to do:
Have a frontend node that boots from a HDD and is able to save data (non-volatile).  Then  I would like to have all the compute nodes setup to boot from either netboot via PXE or boot from a CDROM image.  
Ideally, the cluster would be made up of older PCs I have laying around in our office. I would like to be able to add compute nodes to the cluster as I pick up more spare PCs. I am really planning on running BOINC on the cluster, so only the frontend node will have an actual user on it.  Would like to run Ubuntu and gnome for the desktop.

I have researched PelicanHPC, but it seemed more geared to everything booting from disc, and being volatile (nothing is saved, and is lost during a reboot).  I am wanting to be able to build a cluster that looks like one huge PC to the frontend user.

I have also checked in openmosix, but it has been adandoned it looks like.

What do you guys suggest?

---

