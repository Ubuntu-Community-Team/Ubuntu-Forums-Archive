---
title: "Corporate network with remote authentication"
date: 2010-05-20
forum: General Help
---

### Post by roberthr on 2010-05-20
I would like to address smart guys here to help me out.
It's migrating whole Corporate Windows stations to Ubuntu which is a huge thing so I'd like to do it right and as painless as possible to users.

Here's how it's done now:
Main server are already running Linux for years with DHCP, DNS, IMAP, Postgres and SAMBA.

Windows machines are part of Samba PDC and when user logs in, Windows connects to the user profile on Samba server. When user logs out and logs to another computer, he/she has the same files and settings. Basically, nothing is held on local stations.

All printers on the network are printers with network cards, so they are not attached to any computer. The right printer is set with cmd script when user logs in, which makes it possible to make other printer as default if one is faulty.

What I need at the beginning is how do I set computer to validate user from samba server and mounts home to remote home. I started reading kerberos documentation but I would like to know if there are any such cases or at least if somebody could point me to the right direction.

---

### Post by roberthr on 2010-05-20
bump

---

### Post by roberthr on 2010-05-21
bump... anyone?

---

