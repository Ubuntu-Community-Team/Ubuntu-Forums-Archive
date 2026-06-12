---
title: "NFS replace client's/home"
date: 2009-08-03
forum: General Help
---

### Post by arthur.m on 2009-08-03
Hi all!
Is it possible to mount an nfs share (say /home), insted of a client /home? 
I tried :
sudo -s
mv /home /home.bck
mkdir /home
mount -t nfs <serverip>:/home /home, and it crashes!, i have to do a failsafe session and restore my old /home...
The idea is replace all client's /home with their /home located at the server.
Thanks


Arthur Portas

---

