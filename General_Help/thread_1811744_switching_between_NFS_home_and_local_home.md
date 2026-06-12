---
title: "switching between NFS /home and local /home"
date: 2011-07-25
forum: General Help
---

### Post by SOMDdan on 2011-07-25
I have several Linux computers in my network, and I am tired of having different /home files on each one, so I want to use a NFS share as a common /home. I have Ubuntu server working with an NFS share, and have no problem with editing ***/etc/fstab ***to make the NFS share mount on startup. The challenge I am facing is on my laptops; when they are off the network they obviously can't use the NFS share as a /home. My idea is to have a local copy of the NFS /home directory on each laptop, updated periodically with ***rsync***, that I can mount on /home when the NFS share is unavailable (I also want to do this on my desktops as a backup of /home in case of the server going down). The question is: what is the best way to detect when the NFS share is unavailable? Or in other words, what can I put in a script to make the laptops and desktops detect that the network is unavailable and automatically mount the backup /home directory?

---

