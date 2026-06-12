---
title: "plz help software index is broken"
date: 2010-09-08
forum: General Help
---

### Post by niemann999 on 2010-09-08
i cant open synaptic package which is wierd cuz this the first time i ever was gonna use it can someone plz tell me whats wrong heres the source list
 a error i get when i try this
tyler@nieman999:~$ sudo apt-get install -f
E: Malformed line 57 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.


# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main multiverse restricted universe

# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games

---

### Post by Peter09 on 2010-09-08
Comment out these lines
 
```
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") feisty main
deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games

```
 
by putting a # in front of the line and try again - see if you still get the problem.

---

### Post by niemann999 on 2010-09-08
ok sry bout what u mean by comment out i only had ubuntu for a week so still pretty new

---

### Post by Peter09 on 2010-09-08
Lines that begin with a hash (#) are not considered to be active - just comments - if you look at the sources you will see many lines which have a # in front thes are ignored by the package managers. So change the lines to
 
```
#deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
#deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
#deb [http://packages.dfreer.org]("http://packages.dfreer.org/") feisty main
#deb [http://packages.dfreer.org]("http://packages.dfreer.org/") gutsy main
#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games
```

---

### Post by niemann999 on 2010-09-08
E: Malformed line 57 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
same error i get when i open it

---

### Post by niemann999 on 2010-09-08
tyler@nieman999:~$ #deb [http://packages.dfreer.org](http://packages.dfreer.org) gusty main
tyler@nieman999:~$ #deb [http://packages.dfreer.org](http://packages.dfreer.org) gusty main
tyler@nieman999:~$ #deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
tyler@nieman999:~$ #deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
tyler@nieman999:~$ #deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games
this what u wanted me to do right?

---

### Post by Peter09 on 2010-09-08
Ok do the same for these lines
 
```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

```
 
we really need to identify line 52.

---

### Post by Peter09 on 2010-09-08
Yes - thats right - sorry I thought you had already done it. Try doing the first set and refreshing the sources, then if you still have the error do the same with the second set and refresh the sources and as before try to run synaptic.

---

### Post by niemann999 on 2010-09-08
nope that didnt work i dont know where line 52 would be

---

### Post by plucky on 2010-09-08
> **niemann999 said:**
> nope that didnt work i dont know where line 52 would be

From a terminal ```
gksudo gedit /etc/apt/sources.list
``` and in gedit turn on line numbering **Edit > Preferences** and tick "display line numbers".

You are looking for line 57 but still put a # in front of those lines specified by Peter09.

Good Luck

---

### Post by Peter09 on 2010-09-08
Check that there are no other stray alpha characters in the file, below the lines that you posted. Can you post the file as is now.
 
Also can you do
 
```
sudo apt-get update
```
 
in a terminal and (if there is an error) post it.

---

### Post by niemann999 on 2010-09-08
k its being wierd i type the code u said it waits a bit then nothing happens

---

### Post by niemann999 on 2010-09-08
tyler@nieman999:~$ sudo apt-get update
E: Malformed line 57 in source list /etc/apt/sources.list (URI parse)
tyler@nieman999:~$

---

### Post by Peter09 on 2010-09-08
Need you to do as plucky says and then show us the contents of the file.

---

### Post by niemann999 on 2010-09-08
tyler@nieman999:~$ gksudo gedit /etc/apt/sources.list
tyler@nieman999:~$ 
 it like loads for a lil bit then nothing happens just wierd

---

### Post by niemann999 on 2010-09-08
tyler@nieman999:~$ gedit
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
 well im screwed cuz i cant download anything cuz of this error
any way to bypass this???


if i counted this right this is the corrupt file
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse but i dont no what to do with it?

---

### Post by plucky on 2010-09-08
If **gksudo gedit** doesn't work,does that mean you haven't actually changed the file to put hashes in front of those lines?

Try using nano ```
sudo nano /etc/apt/sources.list
``` Put hashes in front of the specified lines and then CTRL+O and Ctrl+X to write to the file and exit.


The run ```
sudo apt-get update
``` to see if anything changes.


Good Luck

---

### Post by niemann999 on 2010-09-08
okay thanks so much plucky and peter for ur help its working great now

---

