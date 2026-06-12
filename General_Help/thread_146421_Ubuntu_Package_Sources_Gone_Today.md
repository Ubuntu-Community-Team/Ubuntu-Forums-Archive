---
title: "Ubuntu Package Sources Gone Today?"
date: 2006-03-18
forum: General Help
---

### Post by dpaint4 on 2006-03-18
Last night everything seemed fine, and I've made sure I'm connected to the net (wouldn't be posting this if I wasn't), but suddenly Synaptic is acting like none of my sources are available? What could be the cause of that?

This morning when I opened Synaptic, I got this error message in a dedicated window:

```

WARNING! The following problems were found on your system:

W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://www.zeograd.com unstable/main Packages (/var/lib/apt/lists/www.zeograd.com_debian_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.sourceforge.net binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://www.rarewares.org ./ Packages (/var/lib/apt/lists/www.rarewares.org_debian_packages_unstable_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://www.rarewares.org ./ Packages (/var/lib/apt/lists/www.rarewares.org_debian_packages_experimental_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net sid/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_sid_main_binary-i386_Packages) - stat (2 No such file or directory)
```

Why is this?

---

### Post by dpaint4 on 2006-03-18
Okay, so I opened up the repositories menu, unchecked a couple of my non-essential sources and reloaded the list, which worked.

But now the funny thing is that all the packages are showing up as being brand new, with the little star in the left corner of the check-box.

Strange right?

I'm pretty sure it's my fault, but I've got no clue how or why. Anyone with a clue, tell me what you think happened.

---

### Post by sprinkles on 2006-03-18
This exact same thing happened to me yesterday!

---

### Post by dpaint4 on 2006-03-18
[QUOTE=sprinkles]This exact same thing happened to me yesterday![/QUOTE]

Well, that's comforting at least. Thanks!

---

