---
title: "installing firefox 3.5 on 8.10"
date: 2010-03-11
forum: General Help
---

### Post by Piggah on 2010-03-11
Hi all, I'm currently running Ubuntu 8.10 on my system76 notebook as I was having problem after problem after upgrading. However, not having up to date software is a bit of a problem. 

How should I go about installing firefox 3.5 so I can have the most up to date version? Will I need to compile? Can I just install a .deb from karmic repos? Does the current version need removed first?

And there are several other pieces of software I want to stay current with, such as digiKam, but found it impossible because of dependency hell. Should I expect to be downloading tarballs and compiling any programs I want to upgrade past their stage in the 8.10 repos? 

thanks =)

---

### Post by leorolla on 2010-03-11
> **Piggah said:**
> How should I go about installing firefox 3.5 so I can have the most up to date version? Will I need to compile? Can I just install a .deb from karmic repos? Does the current version need removed first?

My way:

Add the following to /etc/apt/preferences:
```
Package: *
Pin: release n=hardy,l=Ubuntu,c=main
Pin-Priority: 901

Package: *
Pin: release n=hardy,l=Ubuntu,c=universe
Pin-Priority: 901

Package: *
Pin: release n=hardy,l=Ubuntu,c=multiverse
Pin-Priority: 901

Package: *
Pin: release n=hardy,l=Ubuntu,c=restricted
Pin-Priority: 901

Package: *
Pin: release n=lucid,l=Ubuntu
Pin-Priority: 90

Package: firefox
Pin: release a=lucid
Pin-Priority: 990

```Add the following to /etc/apt/sources.list.d/lucid.list:
```
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse

```Then:
```
sudo aptitude safe-upgrade -s
sudo aptitude update
apt-cache policy
sudo aptitude safe-upgrade -s

```See if the 3rd command gives low priority for lucid packages, and mentions firefox in the end.
See if 4th command proposes something too crazy.

If it's not too crazy, fine. From now on forget apt-get, because aptitude will find solutions that leave the Hardy setup as little as possible.

If you want to be even safer, try first with interpid instead of lucid, then with lucid.

> **Piggah said:**
> And there are several other pieces of software I want to stay current with, such as digiKam, but found it impossible because of dependency hell. Should I expect to be downloading tarballs and compiling any programs I want to upgrade past their stage in the 8.10 repos?

What?!

---

### Post by lovinglinux on 2010-03-11
You can download Firefox 3.6 from Mozilla and run it, without upgrading your current Firefox. I never tested it on Ubuntu 8.10, but I guess it should work fine.

See [this](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) for instructions.

---

### Post by Piggah on 2010-03-12
> **lovinglinux said:**
> You can download Firefox 3.6 from Mozilla and run it, without upgrading your current Firefox. I never tested it on Ubuntu 8.10, but I guess it should work fine.

See [this](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) for instructions.

this worked. thanks!

---

### Post by leorolla on 2010-03-12
Good that the simpler solution worked for you.

If you want more recent versions of packages with worse post-Hardy dependencies than firefox, you can try my method.

I use it on both of my PC's ;-)

---

