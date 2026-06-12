---
title: "installing gntutls-dev"
date: 2009-07-07
forum: General Help
---

### Post by Gosujii-sama on 2009-07-07
Wine suggests gntutls-dev as a package needed for the building of wine with warcraft (i have the issue in question) but ive searched over the package managers and stuff and cant seem to find a install for this dev package. Quick thoughts on how to get it in?

EDIT:
using sudo apt-get install libgnutls-dev
says im up to date but it still refuses to compile the wine under it. with the schannel error.

checking for gnutls/gnutls.h... yes
configure: error: libgnutls development files not found, no schannel support.
This is an error since --with-gnutls was requested.

---

### Post by Gosujii-sama on 2009-07-08
No ideas?
Gotten zilch on replys so ill just do a full print on data known.

it requiers quote "Make sure that you have also a current version of gntutls-dev installed."
Which im going to assume is really "libgnutls-dev" in which case:

sudo apt-get install libgnutls-dev
[sudo] password for construct:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgnutls-dev is already the newest version.<<<<<<<<<<<<<<<<<<<<<<<<

So im latest on that... then i get this anyway:

checking for gnutls/gnutls.h... yes
configure: error: libgnutls development files not found, no schannel support.
This is an error since --with-gnutls was requested.

This tells me either im looking at wrong dev file or the dev file is not the correct version for this or some other issue i cant think of. Fixes downloads ideas?
i386 ubuntu 8.04 hardy

did a bit of diggin the version its showing for libgnutls-dev is:
libgnutls-dev_2.0.4-1ubuntu2.5_i386.deb on the package file.

---

### Post by Gosujii-sama on 2009-07-09
no one seems to want to reply on this one :P

---

### Post by Gosujii-sama on 2009-07-10
love it when ideas fall apart :D still no ideas?

---

### Post by Gosujii-sama on 2009-07-11
miss my war3 :(

---

### Post by benbillybobjoe on 2009-08-03
Found out the reason it's not on the forums, the orig. post of: 

Quote From: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)
"Make sure that you have gntutls-dev 2.3 or newer installed."

it was misspelled. it's suppose to be (proper form) GNU TLS

---

