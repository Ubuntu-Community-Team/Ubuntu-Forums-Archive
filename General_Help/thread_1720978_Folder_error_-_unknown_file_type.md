---
title: "Folder error - unknown file type"
date: 2011-04-03
forum: General Help
---

### Post by Oval on 2011-04-03
What I have is a samba file server running Ubuntu 10.04. I have a line in the fstab on my laptop, running 10.10, to mount the shares on boot. Everything was working fine until very recently. The sub folders in just one of the shares are an "unknown file type", but only when mounted on boot or with mount command. If I ssh into the server or browse to the server using the menu/places/network...I can access those folders and everything within them without any problems.

I haven't made any changes recently. Any ideas on what's going on?

EDIT: I just checked my desktop, also running 10.10 and using the same line in fstab, it works properly. So, the problem is with the laptop.

EDIT: I still don't know what caused it, but I rebuilt the directory tree and it's all good now.

---

