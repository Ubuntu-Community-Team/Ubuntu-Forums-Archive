---
title: "Section with no Package: header, on almost every update."
date: 2012-05-22
forum: General Help
---

### Post by Martin Hansson on 2012-05-22
On my new Desktop I have Ubuntu 12.04 LTS 64-bit installed and every thing but the upgrades work fine.

Every week I get a warning in the notification area telling me that the upgrades are broken.

Running.
sudo apt-get upgrade ,  gives this answer:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages
E: Paketlistan eller statusfilen kunde inte tolkas eller öppnas.

I fix this once with:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

Is there any way to correct this so that I do not need to enter the Terminal every time  the system needs an upgrade?

---

