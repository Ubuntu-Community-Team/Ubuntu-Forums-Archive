---
title: "E:type 'sudo' is not known on line 62 in source list /etc/apt/sources.list"
date: 2011-05-18
forum: General Help
---

### Post by brangkas on 2011-05-18
the title is the error appeared all in a sudden..
I was trying to install BURG MANAGER, but the installation had not finished,
and update manager window appeared along with message error:;

E:type 'sudo' is not known on line 62 in source list /etc/apt/sources.list

So now, I can't update, i can't run ubuntu software centre or install anythin from terminal.

please anyone could help me how to solve this problem. I am using Maverick Meerkat.

Thank you,
greetings to all Ubuntuers

---

### Post by Plueonic on 2011-05-18
Post the contents of the file; (run the following from a terminal window)
```
cat  /etc/apt/sources.list
```

---

### Post by brangkas on 2011-05-18
> **Plueonic said:**
> Post the contents of the file; (run the following from a terminal window)
```
cat  /etc/apt/sources.list
```

vanhombing@brangkas:~$ cat  /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
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
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free

sudo gpg --keyserver hkp://pgp.mit.edu --recv-keys FA088BA5 && sudo gpg --armor --export FA088BA5 | sudo apt-key add -
sudo apt-get update && sudo apt-get install  burg-manager buc
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
vanhombing@brangkas:

---

### Post by Plueonic on 2011-05-18
Run *gksu gedit /etc/apt/sources.list *to open the file as root and remove the last 5;```
sudo gpg --keyserver hkp://pgp.mit.edu --recv-keys FA088BA5 && sudo gpg --armor --export FA088BA5 | sudo apt-key add -
sudo apt-get update && sudo apt-get install  burg-manager buc
```^They aren't repository lines (you must have added them by mistake)
```

deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free

```You already have a line for the first two and the update manager would complain if there are duplicates. The third one is a repo for lucid.

After saving the file, run *sudo apt-get update *and post back if you get any error messages

---

### Post by brangkas on 2011-05-18
Perfect....

WONDERFULL.. What an Expert...
Thank You so much...

I wish i could be expert as u..

---

### Post by Plueonic on 2011-05-18
Glad i could help.
> **brangkas said:**
> What an Expert...
I'm not an expert either but after using the system for a while, you'll learn to troubleshoot some issues by yourself :)

---

### Post by PWEEZY5 on 2011-07-16
I am getting the exact same message only I was trying to download google chrome. I don't think my issue will be resolved by doing the above reply since I was doing something different. Can anyone help please, I'm new at this.

---

