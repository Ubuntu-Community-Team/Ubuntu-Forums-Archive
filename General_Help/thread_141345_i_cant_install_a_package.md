---
title: "i cant install a package"
date: 2006-03-08
forum: General Help
---

### Post by jeisma on 2006-03-08
hi!

on my first ubuntu install (5.10), im trying to install a package (tbird).

googling my way,  i found i may need to uncomment some lines in the etc/apt/sources.list file. which i did, then run:

$ sudo apt-get update 

which gives this:
================
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'ph.archive.ubuntu.com'
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'ph.archive.ubuntu.com'
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'ph.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
================

i connect to the internet via proxy server. i have the proxy settings setup in my browser. i was wondering if this process (installation) downloads files in the internet and may not be able to connect. are there any settings out there that i may need to configure to be able to do a successful apt-get?

help please?

thank you!

---

### Post by soonindallas on 2006-03-08
look at the "Setting up apt-get to use a http-proxy" section of this wiki page: [https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

telling your browser about the proxy does not help apt-get

---

