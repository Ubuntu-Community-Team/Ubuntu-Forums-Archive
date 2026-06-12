---
title: "Fileserver (win) + ext2/3 + smb"
date: 2006-03-14
forum: General Help
---

### Post by Fisheke on 2006-03-14
Hey,

Our home-network setup is as follows: we have a central fileserver in the basement (win2k3) with a decent raid controller (data there is quasi *unloseable*). All other pc's on the network (besides mine) are windoze-machines.

I was thinking of moving my /home directory to the fileserver (and mount it when booting) (don't want to lose data incase of HD failure). But the home folder is stuffed with symlinks, seen as is't a NTFS (~win2k3) server this doesn't really work.

I was thinking of creating an ext3 partition on the server, but there's no read/write support in windows for it.

Does anyone know a solution that might work here? (/me is quite a noob so i might be missing some things).

---

