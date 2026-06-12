---
title: "How Can I Share Files Between Two Xubuntu Comps?"
date: 2010-01-12
forum: General Help
---

### Post by AlexInBlack on 2010-01-12
I don't know how to share files between my desktop and laptop, each running Xubuntu (9.04 and 9.10, respectively). My friend suggested using LAN, but I've gotten lost going through several Samba, NFS, and FTP guides, most of which seem oriented towards vanilla Ubuntu. Anyone have some suggestions?

---

### Post by Dennis N on 2010-01-12
If the computers are on the same local network together (connected by a router) then install openssh-server on both. On Xubuntu, you can't browse to the other machine with the Thunar file browser, so install the program Filezilla from the repository in order to connect to the other machine. All you need is the IP address of the other machine on the network and your password to connect. You can then make file transfers either direction.

---

### Post by AlexInBlack on 2010-01-13
Thanks that did the trick. :)

---

