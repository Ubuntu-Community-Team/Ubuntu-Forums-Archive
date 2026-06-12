---
title: "upgrade to dapper"
date: 2006-05-11
forum: General Help
---

### Post by shizow on 2006-05-11
i am sorry, but i think this is a stupid question

how do i upgrade to dapper now, from Kubuntu breezy?

---

### Post by awakatanka on 2006-05-11
Open a terminal. then do 

sudo kate /etc/apt/sources.list

Then change everything that is breezy into dapper

Then save it and do :

sudo apt-get update
sudo apt-get dist-upgrade

edit: this is my sources.list maybe helpfull for you :

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
deb http://nl.archive.ubuntu.com/ubuntu dapper main restricted
deb http://nl.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://nl.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://nl.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://nl.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Listen
deb http://theli.free.fr/packages/dapper/ ./

# Koffice 1.5
deb http://kubuntu.org/packages/koffice-15 dapper main

# Amarok 1.4
deb http://kubuntu.org/packages/amarok-14beta3 dapper main

# Compiz
deb http://xgl.compiz.info/ dapper main aiglx
deb http://xgl.compiz.info/ dapper main


```
But make backups of important things because its still beta and everything can break.

---

