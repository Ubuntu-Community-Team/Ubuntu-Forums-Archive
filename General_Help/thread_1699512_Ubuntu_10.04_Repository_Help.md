---
title: "Ubuntu 10.04: Repository Help"
date: 2011-03-03
forum: General Help
---

### Post by SexySara on 2011-03-03
My repositories are really messed up and I don't what I did to mess it up. When I run the code below...

When I try to install things I am getting lots of errors. 
```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://deb.playonlinux.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186
W: Duplicate sources.list entry http://packages.medibuntu.org/ lucid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ lucid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_non-free_binary-i386_Packages)
~$ 



```What can I do to fix my problems? I also included a screen shot of the repositories in Software Sources. I been messing with BeachBit as Root and been toying with Ubuntu Tweak and so I think I messed something up on accident.


Here is my list that I have too...
```

deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties

deb http://ppa.launchpad.net/fta/ubuntu lucid main
# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu lucid partner
deb http://archive.canonical.com/ubuntu lucid-backports partner
deb http://archive.canonical.com/ubuntu lucid-updates partner
deb http://archive.canonical.com/ubuntu lucid-security partner
deb http://archive.canonical.com/ubuntu lucid-proposed partner
deb-src http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid-backports partner
deb-src http://archive.canonical.com/ubuntu lucid-updates partner
deb-src http://archive.canonical.com/ubuntu lucid-security partner
deb-src http://archive.canonical.com/ubuntu lucid-proposed partner


#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free

#PlayOnLinux
deb http://deb.playonlinux.com/ lucid main


#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free main


#Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

``````
GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6GPG error: http://deb.playonlinux.com lucid Release: 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186Failed to fetch cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/dists/lucid/main/binary-i386/Packages.gz  
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/dists/lucid/restricted/binary-i386/Packages.gz  
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```[SIZE=2]**EDIT:::**[/SIZE]
Well after an hour or so on Google and so many different sites, I found the fix. For anyone else who as has this same issue. just check out [THIS SITE]("http://stream-recorder.com/forum/w-gpg-error-http-ppa-launchpad-net-t6741.html") that I found on Google. My computer is now back to normal.

---

### Post by Miscni on 2011-03-31
Thx alot, I was looking for a way to fix that... :)

Cheers

---

