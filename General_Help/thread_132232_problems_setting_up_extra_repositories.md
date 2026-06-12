---
title: "problems setting up extra repositories"
date: 2006-02-17
forum: General Help
---

### Post by newblacknoise on 2006-02-17
I realise this is probably a common newbie problem, but I can't seem to find an answer from searching around the forums or the wiki.

I have just installed breezy, brand new and fresh off a CD. I keep getting these error messages when i start synaptic:

```
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
```

I'll explain what I've done so far to my fresh install of breezy:
1. turned off ipv6 by changing the reference in /etc/modprobe.d/aliases
2. followed the instructions found at [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

that's pretty much it. i can access the internet perfectly well through firefox, so i'm not sure why i can't access the repositories. i have also tried using the source-o-matic at [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic), but to no avail.

ideas?

---

### Post by stalefries on 2006-02-17
Have you tried a 
'sudo apt-get update" yet? That may be it.

Also, it may be that those servers are down. You might want to try again later.

---

### Post by newblacknoise on 2006-02-18
ok, it's sort of working...but not quite. allow me to explain.

but first, my sources.list looks like this:

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://au.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://au.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://au.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

```

i reset my modem/router and my wireless router to factory settings, then ran 'sudo apt-get update' and it ran beautifully, not an error in sight. a little red circle icon appeared up on my task bar saying there were plenty of system updates to get, so i got them, all without a hitch.

however, when i tried to install a package, apt-get couldn't find the server, which seems a little ridiculous, considering i'd JUST connected to it mere seconds before:

```
 [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun 
```

i've got the impression it has something to do with DNS. i'm getting quite lost here. i am able to ping the servers by name or number sometimes, but not others.

can anyone help?

ps - just so that i'm being clear, i have a D-Link DSL-502T modem/router connected to a D-Link DI-624+ wireless router, into which i connect my laptop. i'm trying to set up the ethernet connection properly first, then do the wireless one.

---

