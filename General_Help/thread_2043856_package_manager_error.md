---
title: "package manager error"
date: 2012-08-17
forum: General Help
---

### Post by fidelandche on 2012-08-17
Hi all,

I have the following problem, I have been trying to extract subtitles from an MKV file, so I did a bit of a search and came across this information [http://www.bunkus.org/videotools/mkvtoolnix/downloads.html]("http://www.bunkus.org/videotools/mkvtoolnix/downloads.html")

So I entered the code into a terminal and that was fine, I then went to update my sources list via the package manager, all fine so far but when I went to check for updates, I get the following messages one from synaptic and the other from the package manager, so not really sure on how to fix this problem.

Cheers

---

### Post by raja.genupula on 2012-08-17
Yeah , thats actually problem with your source list . 

open your terminal and type this 

```
sudo gedit /etc/apt/sources.list
```

as displayed in the error message , check the line no for the error . if you are unable to find it , place it here . we will do it for you .

---

### Post by irv on 2012-08-17
If you added these lines to your Source.list. try removing them.
[ATTACH]222822[/ATTACH]

---

### Post by fidelandche on 2012-08-17
this is what I get from the output - # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./ deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./
deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./ deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./

so can I just remove the lines from the list to sort out the error???

@ irv, unable to access the sources list so unable to remove them.

Cheers

---

### Post by irv on 2012-08-17
Open a terminal and type
```
sudo gedit /etc/apt/sources.list
```
enter your password and it will open this file in gedit and you can remove the lines. Be careful not to remove anything else. Save the file and this should get rid of the error.

---

### Post by raja.genupula on 2012-08-17
yup! here we go . actually the lines you have to add is this

```
deb http://www.bunkus.org/ubuntu/precise/ ./
       deb-src http://www.bunkus.org/ubuntu/precise/ ./       
```

so remove those extra lines in the ending i.e  this part

> deb [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./ deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./
deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./ deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./


then save it . now its not going to jump again .

---

### Post by fidelandche on 2012-08-17
Many thanks, now sorted

---

### Post by irv on 2012-08-17
Don't forget to mark this solved.

---

