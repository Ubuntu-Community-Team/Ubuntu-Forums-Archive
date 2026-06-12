---
title: "error in synapic package manager and update manager"
date: 2009-08-23
forum: General Help
---

### Post by Ns_ on 2009-08-23
hallo out there.


im quite new to Linux Ubunto and i got some errors commoing up when im starting up synapic package manager and update manager  and i got no clue how to fix it.


[IMG]http://i27.tinypic.com/1z4v18k.png[/IMG]







[IMG]http://i25.tinypic.com/v6llxj.png[/IMG]



any out there know whats wrong here and how to fix it?



cheers Ns_

---

### Post by michy99 on 2009-08-23
You have some messed up lines in your sources.list file. Post the file and we will see where the error is.```
cat /etc/apt/sources.list
```

---

### Post by Ns_ on 2009-08-23
hmm cant find that file when i search for it ?

---

### Post by drs305 on 2009-08-23
It should print out when you enter the command michy99 gave you in the previous post.

You can open it yourself with the following, which will open gedit with the cursor on the bad line. All lines in sources.list should start with *deb or #*. But it still might be best to post the contents here.

```

gksudo gedit +56 /etc/apt/sources.list

```

It will ask for your password. Type it and hit ENTER, even though you won't see anything.

---

### Post by Ns_ on 2009-08-23
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

For Ubuntu Intrepid (8.10):
```


this is what shows !

---

### Post by drs305 on 2009-08-23
Use the "gksudo gedit" command I gave in the previous post and delete the last line and save the file. Then update the repository list:
> 
[COLOR="Red"]For Ubuntu Intrepid (8.10):[/COLOR]


then 
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Ns_ on 2009-08-23
and there u go now it works :D 

ty for the help :)

---

