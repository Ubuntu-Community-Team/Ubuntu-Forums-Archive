---
title: "cannot find -lbsd"
date: 2006-05-01
forum: General Help
---

### Post by technodolt on 2006-05-01
I can't figure out which forum to post this to, so I'm going to post it to a general one and I'll take constructive criticism on where I should've actually posted it at :)

I'm trying to compile the source of a program I want to use, and I'm getting this error:

/usr/bin/ld: cannot find -lbsd

I'm aware that this means I'm missing the libbsd files, but what I don't know is how to acquire them... I've been trying to find a package I can download with apt-get, but can't seem to figure out if there are any packages containing these files.

Can anyone help?

---

### Post by Essence on 2007-09-13
I ran into this same problem when installing PVS. On the wiki for PVS it said...

> Fix: Simply erase the -lbsd from BDD/ix86-Linux/Makefile.

libbsd is a compatibility library, which seems no longer being needed. It is not provided on Debian and it is empty on Fedora Core. 

It sounds like this is a general issue, and hopefuly should work fine for you. In other words try removing the -lbsd line form your makefile, for whatever it is your building.

---

