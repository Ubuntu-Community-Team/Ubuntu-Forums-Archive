---
title: "fstab mount NFS, but no autoload on boot"
date: 2010-05-16
forum: General Help
---

### Post by WA1DH on 2010-05-16
I have a laptop and I'm trying to set it up so I can make a script to  mount my home file server on it. I can do that using the mount command but it won't let me  unmount it unless I do it from the terminal as root (sudo umount). If I  understand correctly this is because the mount is not in fstab.

Is there a way to allow me to mount a remote volume via NFS using fstab but NOT have it autoload on boot? Everything I read about adding lines to fstab is to load on boot. If my laptop is off my home LAN (most of the time it is) I'm going to get an error message every time I boot it up. I want to use a script to mount it as I please when I'm on the home LAN.

Thanks.

---

### Post by oshunluvr on 2010-05-29
add "noauto" to the fstab line.

Then after booting - issue "sudo mount XXXXX".

---

