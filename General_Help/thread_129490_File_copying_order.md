---
title: "File copying order"
date: 2006-02-13
forum: General Help
---

### Post by julipanno on 2006-02-13
My portable music player plays the tracks in the order they were copied onto the disk, and so naturally I wish to copy the files in alphabetical order. 

Nautilus does this sometimes, but far from always. How does Nautilus determin the copying order? Is there a way to change this?


peace,
Stian

---

### Post by nanotube on 2006-02-13
dont know about nautilus, but you could do it through commandline... :) but that may or may not be an acceptable solution for you.

---

### Post by julipanno on 2006-02-14
[QUOTE=nanotube]dont know about nautilus, but you could do it through commandline... :) but that may or may not be an acceptable solution for you.[/QUOTE]
Thanks for the tip. The cp command does it right all right, which makes me more curious about why Nautilus doesn't. I discovered that Nautilus copies files in the order of last edited, but I haven't found out how to change that.

Is there a way to use or a substitute for cp through an ssh session? That is, I wish to copy a folder from the remote pc to my own in alphabetical order.

---

### Post by ZackDeLaRocha on 2006-02-14
yes, just type scp! :)

usage : scp host@user:/path/to/file  /dest/

---

### Post by nanotube on 2006-02-15
you could also try installing the gui-based package "gftp". allows ftp as well as sftp (ssh-based ftp), through a nice graphical interface.

from commandline, the command "sftp" will do it for you, if you want an interactive ftp session. (scp, as suggested by zack, is a non-interactive one-time copy command, iirc).

---

### Post by julipanno on 2006-02-15
Many thanks.

---

