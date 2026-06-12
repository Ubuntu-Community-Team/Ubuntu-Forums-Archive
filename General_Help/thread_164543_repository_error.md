---
title: "repository error"
date: 2006-04-22
forum: General Help
---

### Post by skinnygmg on 2006-04-22
what did i screw up when adding repositories?  i followed the wiki how to.  it seemed to go well.  but now when i try to install something, or even when i open synaptic, i get the following error:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

thanks in advance

---

### Post by xXx 0wn3d xXx on 2006-04-22
[QUOTE=skinnygmg]what did i screw up when adding repositories?  i followed the wiki how to.  it seemed to go well.  but now when i try to install something, or even when i open synaptic, i get the following error:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

thanks in advance[/QUOTE]

Here's my sources.list, it has all the major repositorys + all security + alot of 3rd party ones. After copy and pasting this sources.list into yours, run sudo apt-get update and then everything should be okay.

---

### Post by skinnygmg on 2006-04-23
that kinda worked.  you have some keys that i don't have.  so now i get this

W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E8DDB29170188C3B

---

### Post by skinnygmg on 2006-04-23
so does anybody know how or where i get authentication keys for the above repositories?

or is this something ubunters just live with?

---

### Post by xXx 0wn3d xXx on 2006-04-23
It looks like you need the public keys for those repositories...does anyone know the keys ?

---

### Post by skinnygmg on 2006-04-23
anyone???

---

