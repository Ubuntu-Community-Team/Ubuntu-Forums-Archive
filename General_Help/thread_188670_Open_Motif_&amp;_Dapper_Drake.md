---
title: "Open Motif &amp; Dapper Drake"
date: 2006-06-04
forum: General Help
---

### Post by Mitush on 2006-06-04
I've upgaraded to Dapper 6.06 from Breezy 5.10 and I am unable to find Open Motif libraries. In Breezy I had Open Motif installed (version 2.2.3) from repositories, but now Synaptic doesn't find libmotif, and when I try apt-get install libmotif, it says lesstif has replaced it. I was using Open Motif before and prefer using it rather than Lesstif. I have all repositories included in sources.list.

Does that mean that Open Motif is not supported in 6.06?

---

### Post by mannheim on 2006-06-04
The open motif libraries are in the dapper "multiverse" repositories, and is called **libmotif3**. You need to enable the multiverse repositories first. Then

```

sudo apt-get install libmotif3

```

libmotif3 and lesstif are mutually exclusive as far as apt are concerned.

---

### Post by Mitush on 2006-06-04
Here is my sources.list file. As you see, multiverse is included
```
#
deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

However, when I try to install...

```
root@serv1:~# apt-get install libmotif3
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmotif3
root@serv1:~# apt-get install libmotif
Reading package lists... Done
Building dependency tree... Done
Package libmotif is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lesstif2
E: Package libmotif has no installation candidate

```

Am I doing something wrong?

---

### Post by mannheim on 2006-06-04
[QUOTE=Mitush]
Am I doing something wrong?[/QUOTE]

I think you have "multiverse" only for the backports repository. I think you need to change

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

```

to

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

---

### Post by Mitush on 2006-06-04
I replaced
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

```
with 
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

```
and I think it finds libmotif3 now. Thanks for your help mannheim.

---

### Post by mannheim on 2006-06-04
You're welcome.

---

