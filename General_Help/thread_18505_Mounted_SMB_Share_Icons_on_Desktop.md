---
title: "Mounted SMB Share Icons on Desktop"
date: 2005-03-07
forum: General Help
---

### Post by haydenlaptop on 2005-03-07
I was wondering how I can get a shortcut to mounted smb shares to appear on my desktop once I mount them.

I am using Warty with Gnome.

---

### Post by ubuntu_demon on 2005-03-10
[QUOTE=haydenlaptop]I was wondering how I can get a shortcut to mounted smb shares to appear on my desktop once I mount them.

I am using Warty with Gnome.[/QUOTE]
 just create a launcher (right mouse button -> create launcher)

and in the field command fill in :

nautilus /mnt/mountedpartition

where /mnt/mountedparition the location of your mounted partition is

look here for instructions how to mount smb shares :
[http://www.ubuntuguide.org/#automountnetworkfolder](http://www.ubuntuguide.org/#automountnetworkfolder)

---

