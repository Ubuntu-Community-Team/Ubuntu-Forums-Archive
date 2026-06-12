---
title: "Gnome VFS FTP time-out / NOOP"
date: 2009-12-10
forum: General Help
---

### Post by Lieter on 2009-12-10
Hi,

I'm getting 'server closed connection' when I try to save a file to FTP via GVFS. It appears that GVFS does not send NOOP or PWD commands(haven't tested it yet) to keep the connection open(active). 

Is there a way to make GVFS do that? I've looked in gconf and  but I can't find any related settings.

Thanks in advance for any answers :)

---

