---
title: "Help with 9.04 sources list"
date: 2011-09-16
forum: General Help
---

### Post by Dragonseer on 2011-09-16
Hi,

Just trying to update my sources.list so an archived server is included in the synaptic package manager?? I tried to edit /etc/apt/sources.list in the terminal but it just returned a blank page in gedit.  Any help would be appreciated!!

---

### Post by editheraven on 2011-09-16
**Ubuntu Sources List Generator**



[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by varunendra on 2011-09-16
> **editheraven said:**
> **Ubuntu Sources List Generator**
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Unfortunately, the linked page does not list 9.04 since it was not an LTS release.

@Dragonseer,
If you have the installation media that you used to install the OS, you can simply boot into a live session from it and copy the file from there. Here's the contents from **sources.list** file of 9.10, I think replacing 'karmic' with 'jaunty' should do the job:
```
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb http://archive.ubuntu.com/ubuntu karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu karmic main restricted

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu karmic universe
# deb-src http://archive.ubuntu.com/ubuntu karmic universe
# deb http://archive.ubuntu.com/ubuntu karmic-updates universe
# deb-src http://archive.ubuntu.com/ubuntu karmic-updates universe
# deb http://security.ubuntu.com/ubuntu karmic-security universe
# deb-src http://security.ubuntu.com/ubuntu karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu karmic multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic multiverse
# deb http://archive.ubuntu.com/ubuntu karmic-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-updates multiverse
# deb http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse


```

---

