---
title: "error when searching w/ apt-get"
date: 2006-04-06
forum: General Help
---

### Post by th3gh05t on 2006-04-06
hi, 

i get the following error when i try and search for a package:

> derek@ghost:~$ sudo apt-cache search gaim
gaim-data - multi-protocol instant messaging client - data files
gaim - multi-protocol instant messaging client
nautilus-sendto - provide integration between nautilus, evolution, and gaim
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packa ges (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/ma in Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_m ain_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/re stricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-upd ates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Package s (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No suc h file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/va r/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breez y_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_b reezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages  (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Package s) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/v ar/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packa ges) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backpor ts_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-b ackports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-bac kports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-b ackports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var /lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such fi le or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/ lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)

Why can't it find these files? It was working before, what has changed?

Thanks, th3gh05t

---

### Post by aysiu on 2006-04-06
Have you tried this? ```
sudo apt-get update
apt-cache search gaim
```

---

