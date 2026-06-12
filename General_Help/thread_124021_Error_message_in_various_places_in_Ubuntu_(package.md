---
title: "Error message in various places in Ubuntu (package manager etc)"
date: 2006-01-31
forum: General Help
---

### Post by BurningToad on 2006-01-31
Hello, I keep getting this message and it seems to be causing a number of problems.  It always comes up when I open up the synaptic package manager and sometimes comes up when I open file navigation and such.  Any idea what the problem is?

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

---

### Post by kaamos on 2006-01-31
The package manager is just trying to check the packages on the ubuntu installation cd. You can disable the cd as an installation source (all the packages are available from the online repos) in synaptic->settings->repositories

---

