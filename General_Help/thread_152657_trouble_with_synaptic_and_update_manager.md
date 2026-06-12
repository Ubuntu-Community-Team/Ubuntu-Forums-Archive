---
title: "trouble with synaptic and update manager"
date: 2006-03-30
forum: General Help
---

### Post by harys on 2006-03-30
hi, i have this information when i enter synaptic package manager :

The following problems were found on your system:
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

other problem found in the system via the synaptic package manager
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

these other messages appeared when i want to update the system by the red pop up in the menu bar of gnome :
You have 2 broken packages on your system!
Use the "Broken" filter to locate them.

what could i do to make the system work normally. thanks. harys

---

### Post by Zimmer on 2006-03-30
This message means the repositories mentioned are not available/not responding. They look like the EasyUbuntu repository names ...
The simple answer:
You will need to wait until the repositories come back online, if you need to upgrade packages from those particular locations.

---

