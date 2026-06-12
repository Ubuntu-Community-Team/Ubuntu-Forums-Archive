---
title: "Where Does Nautilus Mount Its Remote Connections?"
date: 2010-07-20
forum: General Help
---

### Post by Bradj47 on 2010-07-20
Meaning: When I use the Connect to Server feature with SSH or FTP, is there a mount point for the remote location? I checked /media and /dev and didn't see anything that looked like my connection. And when I keep hitting the UP arrow in Nautilus I just end up in / on the remote location.

---

### Post by cj.surrusco on 2010-07-20
It doesn't mount them like normal file systems. To mount FTP's at a specific location, I use [curlftpfs]("http://curlftpfs.sourceforge.net/").

---

### Post by JustinR on 2010-07-20
Nautilus uses Gnome Virtual File System to mount network extensions in this directory: (last time I checked)

/home/USERNAME/.gvfs/

---

### Post by lordskid on 2010-07-20
I just checked.... and it is still there

~/.gvfs/

thanks justin I wanted to ask the same question.

---

### Post by JustinR on 2010-07-20
Your welcome.

---

### Post by emrys.r on 2010-08-31
> **JustinR said:**
> Nautilus uses Gnome Virtual File System to mount network extensions in this directory: (last time I checked)

/home/USERNAME/.gvfs/


thnks! just what i was looking for.

on lucid - dell studio 17.

---

