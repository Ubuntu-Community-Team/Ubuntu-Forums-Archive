---
title: "really bad problems"
date: 2011-03-18
forum: General Help
---

### Post by scaredycrow on 2011-03-18
okay so, i first noticed when i tried to get mono via sudo apt-get install mono
 
i got the error

```
~$ sudo apt-get install mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mono' has no installation candidate

```then i tried to get it through the software center and i noticed the software center wasn't opening....

so i tried searching to find if someone else had the proroblem, they did, one solution was to reinstall python but if i open syapitic software i get the error 

```
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```what the hell happend to my PC?!?!?


EDIT: never mind i gave up and reinstalled.

---

### Post by SmilePiper on 2011-03-18
I ran into your second problem just yesterday and was able to solve it by opening the terminal and opening an Administrater browser by typing:
gksudo nautilus

I then navigated to the folder /etc/apt/sources.list.d and deleted any files with the name that I was having problems with.

---

### Post by directhex on 2011-03-18
> **scaredycrow said:**
> okay so, i first noticed when i tried to get mono via sudo apt-get install mono
 
i got the error

```
~$ sudo apt-get install mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mono' has no installation candidate

```

There is no binary package called "mono". You likely want "mono-complete" if you want everything.

> then i tried to get it through the software center and i noticed the software center wasn't opening....

so i tried searching to find if someone else had the proroblem, they did, one solution was to reinstall python but if i open syapitic software i get the error 

```
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

what the hell happend to my PC?!?!?

run "cat /etc/apt/sources.list" and paste the result.

---

### Post by scaredycrow on 2011-03-18
> **directhex said:**
> There is no binary package called "mono". You likely want "mono-complete" if you want everything.

yep, that works thanks.

> run "cat /etc/apt/sources.list" and paste the result.sorry, what do you mean by run (new to ubuntu) as in, type that into the terminal?

EDIT okay, i assume so i got this from the terminal

[SPOILER]~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
deb-src [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
deb [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
deb-src [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
[/SPOILER]

---

### Post by alexfish on 2011-03-18
hi all,
 some time ago got a email from , well known, sources, what do you think of,
having spent so much time at trying to install mono , and all the bits , and there are more bits to mono, than the parts to  bridges it cant cross,
/home/eddie/cudadriver_3.0-beta1_linux_32_195.17-beta.run  /home/eddie/cudatoolkit_3.0-beta1_linux_32_ubuntu9.04.run    /home/eddie/gpucomputingsdk_3.0-beta1_linux.run this is the drivers  i have,from nvidia try mono in the software center see what you think  of it,
Totally give up on trying to install install all of the above,

That was two years ago , and the only thing that mono understands , is no,

just like windows , 

arghhh.

alexfish.

---

### Post by directhex on 2011-03-19
> **alexfish said:**
> hi all,
 some time ago got a email from , well known, sources, what do you think of,
having spent so much time at trying to install mono , and all the bits , and there are more bits to mono, than the parts to  bridges it cant cross,
/home/eddie/cudadriver_3.0-beta1_linux_32_195.17-beta.run  /home/eddie/cudatoolkit_3.0-beta1_linux_32_ubuntu9.04.run    /home/eddie/gpucomputingsdk_3.0-beta1_linux.run this is the drivers  i have,from nvidia try mono in the software center see what you think  of it,
Totally give up on trying to install install all of the above,

That was two years ago , and the only thing that mono understands , is no,

just like windows , 

arghhh.

alexfish.

Try again in English.

---

### Post by directhex on 2011-03-19
> **scaredycrow said:**
> deb [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
deb-src [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
deb [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner
deb-src [http://archive.canocical.com/lucid](http://archive.canocical.com/lucid) partner

Here are your defective lines.

They should read:

```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```

To fix, from your terminal, type "sudo gedit /etc/apt/sources.list" and replace those four lines of yours with a copy-paste from my two lines above. Then run "sudo apt-get update". This should be enough to make the software center work again.

---

