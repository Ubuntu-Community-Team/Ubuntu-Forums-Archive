---
title: "Install Java?"
date: 2009-09-15
forum: General Help
---

### Post by ChaosChris2009 on 2009-09-15
How do I install Java in Kubuntu 9.04?

Command preferred, thanks

---

### Post by conehead77 on 2009-09-15
```

sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-jdk

```

or

```

sudo apt-get install openjdk-6-jre
sudo apt-get install openjdk-6-jdk

```

for firefox plugin:

```
sudo apt-get install sun-java6-plugin
```

---

### Post by uylug on 2009-09-15
> **conehead77 said:**
> ```

sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-jdk

```or

```

sudo apt-get install openjdk-6-jre
sudo apt-get install openjdk-6-jdk

```for firefox plugin:

```
sudo apt-get install sun-java6-plugin
```

That's right!

---

### Post by ChaosChris2009 on 2009-09-15
This is what I get no matter which I try

> [sudo] password for chris:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


---

### Post by MR_MUSHROOM on 2009-10-04
ChaosChris2009 it looks like your /etc/apt/sources.list file is not complete for these packages dependencies.

TIP #1  To list your sources.list (source fore your packages).

```
sudo cat /etc/apt/sources.list
```

This is how mine looks like
```

# deb cdrom:[Kubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://se.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy universe
deb http://se.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://se.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://se.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://se.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://se.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ hardy-security multiverse

#medibuntu repository LAGT DIT SJELV :)
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

```


TIP #2 To backup your sources.list to Home Directory.
If any thing goes wrong. Replays your_user_name in the code with
your user name.

```
sudo cp /etc/apt/sources.list /home/your_user_name/
```

edit it from your preferd text editor or via synaptic or your
program you are using.

This is what i use (Kubuntu hardy)
Some people wold hang me fore this :)

```
sudo kate /etc/apt/sources.list
```

more correct way is

```
sudo vi /etc/apt/sources.list
```

TIP # 3 To close vi (editor) ctrl+zz
visit [http://ss64.com/bash/vi.html](http://ss64.com/bash/vi.html) fore online vi commands.
OR
```
man vi
```

if you want a special package use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to
Search fore it.


Hope this helps and God luck.

---

