---
title: "synaptic"
date: 2011-07-14
forum: General Help
---

### Post by firejackson1 on 2011-07-14
keep getting yellow triangle and it brings me to synaptic package manager and when i press reload i get this


GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAFailed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by wildmanne39 on 2011-07-14
> **firejackson1 said:**
> keep getting yellow triangle and it brings me to synaptic package manager and when i press reload i get this


GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAAFailed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.Hi, this error is because that package it not on that server, you can open synaptic click on setting, repositories, other software and uncheck the these two or delete them.
> Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...source/Sources](http://ppa.launchpad.net/team-xbmc/p...source/Sources) 404 Not Found
Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...amd64/Packages](http://ppa.launchpad.net/team-xbmc/p...amd64/Packages) 404 Not Found
The gpg key error try this.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
and replace KEYID with the number shown in the error message.

---

### Post by plucky on 2011-07-15
> Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

And also un-tick the CD-roms as a source.

Good Luck

---

