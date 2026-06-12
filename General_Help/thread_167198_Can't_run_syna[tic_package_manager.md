---
title: "Can't run syna[tic package manager"
date: 2006-04-27
forum: General Help
---

### Post by tommcd on 2006-04-27
Yesterday synaptic ran fine. It notified me of a bunch of updates, but I did not install them yet because I first went to ubuntuguide.org and installed flash, multimedia codecs, etc.
Today I boot up, the red icon in notification area is gone. When I try to run synaptic I get this message:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

I don't have a clue what this means. Did I mess something up? Any help appreciated, thanks.

---

### Post by unnes on 2006-04-27
Open up your terminal, and enter> sudo apt-get update

See if this resolves your problem.

---

### Post by nanotube on 2006-04-27
or simply hit the "reload" button once synaptic starts up. :)

---

### Post by tommcd on 2006-04-27
Thanks , hitting the reload button worked. Sorry for the n00b type question. I'm just trying to learn this OS.
Is there any way to damage the system by, for example, downloading codecs or programs more than once? Would this cause errors, or do they just install rewrite the old files?

---

### Post by unnes on 2006-04-27
> or simply hit the "reload" button once synaptic starts up.

lol I guess the fact that I'm new to Ubuntu is showing, huh?  :cool:

---

### Post by nanotube on 2006-04-28
[QUOTE=unnes]lol I guess the fact that I'm new to Ubuntu is showing, huh?  :cool:[/QUOTE]
haha yea. i ran into the same a few months ago when i was new. :)

---

