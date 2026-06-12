---
title: "problem getting updates"
date: 2011-05-02
forum: General Help
---

### Post by mickynuu on 2011-05-02
hi im having problems getting updates for mm 10-10 everytime i check for updates i get this message any help would be appreciated ive tried posting before but dont know if it was in the right forum heres the message i keep getting  W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release)  Unable to find expected entry  deb-src/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2011-05-02
> **mickynuu said:**
> hi im having problems getting updates for mm 10-10 everytime i check for updates i get this message any help would be appreciated ive tried posting before but dont know if it was in the right forum heres the message i keep getting  W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release)  Unable to find expected entry  deb-src/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Try a different server.

Open Software Sources and on the First Page Change the Download server and then "Reload" which will download the new Index Files.

Good Luck

---

### Post by mickynuu on 2011-05-02
hi ive tried that changing the server but still get the message repository files failed to down load and the same detailed message i changed the server a few times it downloads the updates all but the last couple of kb s checked the internet connection its ok :(

---

### Post by plucky on 2011-05-02
Can you post your sources.list?

Open a terminal and ```
cat /etc/apt/sources.list
```

> Unable to find expected entry deb-src/source/Sources in Meta-index file (malformed Release file?)

Can you make sure the **Source Code** box isn't ticked in the first page of Software Sources.

---

### Post by mickynuu on 2011-05-02
> **plucky said:**
> Can you post your sources.list?

Open a terminal and ```
cat /etc/apt/sources.list
```

Can you make sure the **Source Code** box isn't ticked in the first page of Software Sources.
heres the sources list the box was unchecked     mick@mick-pc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
mick@mick-pc:~$   hope this helps ???!!!:)

---

### Post by plucky on 2011-05-02
Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and remove ```
deb-src http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner deb-src http://archive.canonical.com/ubuntu maverick partner
```

Then run ```
sudo apt-get update
```

Good Luck

---

### Post by mickynuu on 2011-05-02
> **plucky said:**
> Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and remove ```
deb-src http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner deb-src http://archive.canonical.com/ubuntu maverick partner
```Then run ```
sudo apt-get update
```Good Luck
thanks very much that appears to have done the trick :D:D

---

