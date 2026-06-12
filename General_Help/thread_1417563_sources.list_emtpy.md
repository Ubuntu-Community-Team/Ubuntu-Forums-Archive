---
title: "sources.list emtpy ?"
date: 2010-02-27
forum: General Help
---

### Post by CatchItBaby on 2010-02-27
i Installed fresh Ubuntu 9.10 and after that i checked my sources.lst file i found that it is empty ?

Is it ok ? or i m facing any error

---

### Post by bruno9779 on 2010-02-27
It shouldn't be empty.

have you opened it from command line? If so, a typo in the path, would open a new file.

example:

```
sudo gedit /etc/apt/sources.lst
```

would open the right file.

```
sudo gedit /etc/apt/souces.lst
```

would open a blank file, with a name very similar to sources.lst


If you have indeed opened the right file, and it is empty, consider using this:

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

it is a pretty good interface to generate a custom sources.lst

---

### Post by CatchItBaby on 2010-02-27
It open emtpy file and in terminal it give these lines

[IMG]http://i46.tinypic.com/szv2nc.jpg[/IMG]


These are errors ?

---

### Post by _khAttAm_ on 2010-02-27
try /etc/apt/sources.list

---

### Post by CatchItBaby on 2010-02-27
yes i opened that file it is emtpy 

and i just installed ubuntu in my pc ..

i m afraid that something missing

---

### Post by _khAttAm_ on 2010-02-27
Use [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to generate your sources.list

---

### Post by Primefalcon on 2010-02-27
Just to confirm

Run
```
gedit /etc/apt/sources.list
```

and it's blank yes?

also are you running Ubuntu 9.10 Karmic Koala on 32 bit?

NVM _khAttAm_ posted a nice link, I was goin g to give you the contents of my sources file but no longer needed :-)

---

### Post by CatchItBaby on 2010-02-27
whenever i press sudo apt-get update i got this

[B]W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/B]

---

### Post by CatchItBaby on 2010-02-27
> **Primefalcon said:**
> Just to confirm

Run
```
gedit /etc/apt/sources.list
```

and it's blank yes?

also are you running Ubuntu 9.10 Karmic Koala on 32 bit?

NVM _khAttAm_ posted a nice link, I was goin g to give you the contents of my sources file but no longer needed :-)

[IMG]http://i46.tinypic.com/2lwtcgk.jpg[/IMG]

---

### Post by Primefalcon on 2010-02-27
about the 32 bit just try 

```
uname -m
```

if it says i686

I suppose you could use the same as I am

run

sudo gedit /etc/apt/sources.list

and copy and paste the following

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

---

### Post by CatchItBaby on 2010-02-28
Thanks

---

