---
title: "Install Paths"
date: 2009-12-02
forum: General Help
---

### Post by klikevil on 2009-12-02
Is there a way i can make synaptic or apt-get install to a network location i have some network shares mapped on startup via fstab and i'd like to install KDE on to the network rather than store it locally since it's 400 megs, or at least change the install path to my other partition if i can't install it over to the network.

---

### Post by dcstar on 2009-12-02
> **klikevil said:**
> Is there a way i can make synaptic or apt-get install to a network location i have some network shares mapped on startup via fstab and i'd like to install KDE on to the network rather than store it locally since it's 400 megs, or at least change the install path to my other partition if i can't install it over to the network.

Quickest way would be to replace the cache folder with a Symlink to the network share on all machines that you want to use.

A better way would be to set up a repository managed by one machine that all others access.

---

