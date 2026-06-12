---
title: "Precise Automatic Update -authentication not prompted?"
date: 2012-08-20
forum: General Help
---

### Post by twogeo on 2012-08-20
What have I missed?
 Precise, 2D Unity, Auto-login to a single admin account. 
Update Manager set to present all updates daily. 
Synaptic used for individual package management otherwise. 
Password always prompted for by that application at all operations. 

At the last couple of update presentations, Update Manager didn't prompt for admin password when okayed to install updates. 
From memory (I don't often manually invoke Update Manager) Update Manager *did* prompt for password when last used to update packages manually.  

Another machine running Lucid always prompts for auto update installs. 
 I can't understand how this Precise behaviour could be by design. 
Any help with where to begin troubleshooting?

---

### Post by twogeo on 2012-08-20
A launchpad question answered this just now:

Since 12.04,  Update Manager is privileged via Policy Kit to update installed software without authentication.

New installs, including kernels, still need authentication.

---

