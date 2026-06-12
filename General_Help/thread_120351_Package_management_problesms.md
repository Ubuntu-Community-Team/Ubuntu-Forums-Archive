---
title: "Package management problesms"
date: 2006-01-21
forum: General Help
---

### Post by dube.on.bass on 2006-01-21
hello once again,
i open synaptics and it gives me an error message stating:
**We have found the following problems with your pc:**
[B]W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
[/B]
now, i do know that i checked the repositories list and it told me that it was downloading packages for 5.4H.H. but i dont know how to fix this problem? any advice?

---

### Post by poiuytr on 2006-01-21
I just had a similar problem, after upgrading Breezy to its new kernel.  Just go into Repositories in Synaptic and click on Settings to make sure all possible repositories are showing, and then, you may need to tweak what you have clicked.

I had to reenable one which had become disabled (probably from the new kernel upgrade operation?)  Dunno, but once I re-enabled everything I wanted it seems to be working fine again.

---

### Post by GeneralZod on 2006-01-21
Also remember to click "Reload" in synaptic after making any changes to  the sources.list.

---

### Post by rockstar on 2006-01-26
First of all, I don't know what animal I am, I think I might be a badger.  What is the difference between animals? What do the animals represent?

Also I don't know how to install programs I installed off of sourceforge.net.  well, I guess I don't know how to install any programs.

---

### Post by public_void on 2006-01-26
The animals are the releases of Ubuntu, the lastest it Breezy Badger 5.10, the next new release will be Dapper Drake. Previous ones have been Warty Warthog 4.10 and Hoary Hedgehog 5.04 (You'll see them in the previous releases forum). If you downloaded an ISO, or ordered the CD then it will have Breezy on it.

See this [link](http://www.psychocats.net/linux/installingsoftware.php) from aysiu sig.

---

### Post by rockstar on 2006-01-26
I have discovered I'm a badger.  Where do I type code?

---

