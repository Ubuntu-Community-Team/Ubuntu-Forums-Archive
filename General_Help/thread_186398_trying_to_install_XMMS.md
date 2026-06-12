---
title: "trying to install XMMS"
date: 2006-06-01
forum: General Help
---

### Post by Trollhammer on 2006-06-01
I am trying to install XMMS from source since I don't know where to find a pre compiled one for Ubuntu. I tried ./configure and it said I didn't have a Compiler so I did a search on GCC and typed "apt-get install build-essential" and it said it installled I think.. But when I ./configure XMMS it still says I have no compiler. Any idea on how I can get this thing up and running?

---

### Post by joshrobinson on 2006-06-01
[QUOTE=Trollhammer]I am trying to install XMMS from source since I don't know where to find a pre compiled one for Ubuntu. I tried ./configure and it said I didn't have a Compiler so I did a search on GCC and typed "apt-get install build-essential" and it said it installled I think.. But when I ./configure XMMS it still says I have no compiler. Any idea on how I can get this thing up and running?[/QUOTE]

click applications, add remove then click sound and video, xmms is at the botton of the list.. it will install it right like that for you

---

### Post by zachtib on 2006-06-01
sudo apt-get install build-essential?

also, try beep, its an updated xmms:

sudo apt-get install beep-media-player

---

### Post by joshrobinson on 2006-06-01
[QUOTE=zachtib]sudo apt-get install build-essential?

also, try beep, its an updated xmms:

sudo apt-get install beep-media-player[/QUOTE]

i think you might need to have him enable more repo's for beep

---

### Post by Trollhammer on 2006-06-01
Thanks for the help. I think this program will be fine if I can figure out how to get mp3s working in it.

---

### Post by joshrobinson on 2006-06-01
[QUOTE=Trollhammer]Thanks for the help. I think this program will be fine if I can figure out how to get mp3s working in it.[/QUOTE]


they should work automatically, its not like redhat or other distro's where you have to install the codec's manually.. at least they always worked fine for me in ubuntu

---

### Post by zachtib on 2006-06-01
[QUOTE=joshrobinson]i think you might need to have him enable more repo's for beep[/QUOTE]

my sources.list (stolen from someone else on this board):
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
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# Penguin Liberation Front (PLF)
deb http://theli.free.fr/packages/dapper/ ./

# Dapper PLF repository (not yet available)
# deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# Compiz (packages, GPG key: 31A5F97FED8A569E)
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main aiglx
deb http://compiztools.free.fr/debian unstable main

# Gaim 2 Beta 3
deb http://people.ubuntu.com/~seb128/deb ./

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Official Wine
# deb http://wine.sourceforge.net/apt/ binary/

# Wine Dapper
deb http://wine.lowvoice.nl/apt dapper main
```

---

### Post by joshrobinson on 2006-06-01
i use the same site as the person you stole that from.. the ubuntu source-o-matic is nice :-)

sites down right now tho.. i needed it earlier

---

