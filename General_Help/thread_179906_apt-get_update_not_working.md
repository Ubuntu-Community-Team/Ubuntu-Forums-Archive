---
title: "apt-get update not working"
date: 2006-05-21
forum: General Help
---

### Post by monkblah on 2006-05-21
Hi,

My "apt-get update" command stopped working. It kept giving me errors whenever I ran it & would not allow me to install new apps.

So I generated a new source.list file with the ubuntu source-o-matic page ([http://www.ubuntulinux.nl/source-o-matic)](http://www.ubuntulinux.nl/source-o-matic)). But it still does not work; I get the following errors now:

```

$ sudo apt-get update
Password:
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy Release
Get:3 http://kubuntu.org breezy Release.gpg [191B]
Ign http://kubuntu.org breezy Release.gpg
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://kubuntu.org breezy Release
Ign http://people.ubuntu.com ./ Release.gpg
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy/main Packages
Ign http://kubuntu.org breezy Release
Ign http://people.ubuntu.com ./ Release
Get:5 http://mirror.ubuntulinux.nl breezy-seveas Release.gpg [309B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy/multiverse Sources
Ign http://kubuntu.org breezy/main Packages
Ign http://people.ubuntu.com ./ Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://mirror.ubuntulinux.nl breezy-seveas Release
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Hit http://us.archive.ubuntu.com breezy-updates/universe Packages
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-updates/universe Sources
Ign http://kubuntu.org breezy/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Sources
Hit http://people.ubuntu.com ./ Packages
Err http://kubuntu.org breezy/main Packages
  404 Not Found
Err http://kubuntu.org breezy/main Sources
  404 Not Found
Get:6 ftp://cipherfunk.org breezy Release.gpg [189B]
Get:7 ftp://ftp.free.fr breezy Release.gpg
Ign http://mirror.ubuntulinux.nl breezy-seveas Release
Hit http://kubuntu.org breezy/main Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://mirror.ubuntulinux.nl breezy-seveas/all Sources
Hit http://kubuntu.org breezy/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Err ftp://ftp.free.fr breezy Release.gpg
  Read error - read (104 Connection reset by peer)
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Hit ftp://cipherfunk.org breezy Release
Ign ftp://cipherfunk.org breezy Release
Get:8 ftp://cipherfunk.org breezy/main Packages
Ign ftp://cipherfunk.org breezy/main Packages
Get:9 ftp://ftp.free.fr breezy Release
Get:10 ftp://cipherfunk.org breezy/main Sources
Ign ftp://ftp.free.fr breezy Release
Ign ftp://cipherfunk.org breezy/main Sources
Get:11 ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Packages
Get:12 ftp://ftp.free.fr breezy/non-free Packages
Get:13 ftp://cipherfunk.org breezy/main Packages [12.7kB]
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:14 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:15 ftp://cipherfunk.org breezy/main Sources [3765B]
Get:16 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Get:17 ftp://ftp.free.fr breezy/free Packages [545B]
Err ftp://ftp.free.fr breezy/free Packages
  Read error - read (104 Connection reset by peer)
Get:18 http://users.lichtsnel.nl breezy-seveas Release.gpg [309B]
Hit http://users.lichtsnel.nl breezy-seveas Release
Ign http://users.lichtsnel.nl breezy-seveas Release
Hit http://users.lichtsnel.nl breezy-seveas/all Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Fetched 17.3kB in 6s (2591B/s)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/Release.gpg  Read error - read (104 Connection reset by peer)
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/breezy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/breezy/main/source/Sources.gz  404 Not Found
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  Read error - read (104 Connection reset by peer)
Reading package lists... Done
W: GPG error: http://mirror.ubuntulinux.nl breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A12342366
W: GPG error: ftp://cipherfunk.org breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF1234234234
W: GPG error: http://users.lichtsnel.nl breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A122341234466
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
$


```

This is what my (new) sources.list file says:

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
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://users.lichtsnel.nl/~seveas breezy-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror.ubuntulinux.nl breezy-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu breezy main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest breezy main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest breezy main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest breezy main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# OpenOffice.org 2 final packages (packages)
deb http://people.ubuntu.com/~doko/OOo2/ ./



```


Can you help me & tell me what my source.list file should say to work correctly?  Thank you.

---

### Post by Perfect Storm on 2006-05-21
You need to verify the keys for the specific places, check 

>  gpg --keyserver subkeys.pgp.net --recv KEY
 gpg --export --armor KEY | sudo apt-key add -

as it says in your sourcelist.


> # Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free


You might check for a mirror.

---

