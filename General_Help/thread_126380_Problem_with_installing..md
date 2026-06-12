---
title: "Problem with installing."
date: 2006-02-06
forum: General Help
---

### Post by jaylion on 2006-02-06
When i try to install any program through synatic or using sudo apt-get install this error message pop up and the install fail:
```
make: Leaving directory `/usr/share/horde2/turba/po'
dpkg: error processing turba (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 turba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
got any idea? it was working before. I am new..:(

---

### Post by aysiu on 2006-02-06
I have no idea, but usually when people have weird apt-get problems, they stem from a bad sources.list (incompatible sources). Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by jaylion on 2006-02-06
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```
This is what's shown.
I don't think it's the problem with the source coz i could get the file downloaded..
just before the error messages there is bunch other errors show up regrading the language thing???

```
Setting up turba (1.2.5-1) ...
make: Entering directory `/usr/share/horde2/turba/po'
Checking for os ...
Compiling locale ar_SY:
399 translated messages, 47 untranslated messages.
  ... done

Compiling locale bg_BG:
265 translated messages.
  ... done

Compiling locale ca_ES:
263 translated messages.
  ... done

Compiling locale cs_CZ:
261 translated messages.
  ... done

```
i don't know if this is normal. :(

---

