---
title: "apt-get issue"
date: 2010-10-25
forum: General Help
---

### Post by arty0 on 2010-10-25
Problem solved

Hi there,
I just changed (not upgraded, I made a clean install on a new hard drive) from 9.10 to 10.10 and I have a serious problem.

I just can't install new packages.
Neither apt-get nor synaptic can find any package. I either get a "E: Unable to locate package <package_name>", or "E: Package <package_name> has no installation candidate"

For example when I type *sudo apt-get install emacs23* , I get this output:> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package emacs23
And the synaptics package manager only lists the packages I already have.

I searched these forums and googled my error message, but I couldn' t find anything helpful.

The only thing I know is that this is not a network/proxy problem, I am behind a proxy but I have set the http/https/ftp_proxy environment variables, and I have a working network connection, as I am actually posting from the same computer.

Help much appreciated, thanks in advance.

-- 
Arty0

---

### Post by aeronutt on 2010-10-25
What does your sources list (/etc/apt/sources.list) look like?

---

### Post by arty0 on 2010-10-25
It looks like this: 
> #deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

---

### Post by sikander3786 on 2010-10-25
Sources.list seems fine. Try,

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Post back the output if not successful.

---

### Post by arty0 on 2010-10-25
Wow, I got a lot of warnings and errors while running the update command.
It's  "407  Proxy Authentication Required [IP: 10.40.42.61 3128]".

---

### Post by arty0 on 2010-10-25
up ?

---

### Post by sikander3786 on 2010-10-25
> **arty0 said:**
> up ?
Please see post # 7 in this thread.

[http://wwww.ubuntuforums.org/showthread.php?p=9785363](http://wwww.ubuntuforums.org/showthread.php?p=9785363)

---

### Post by arty0 on 2010-10-26
Seems to work great.

Thanks a lot !

---

