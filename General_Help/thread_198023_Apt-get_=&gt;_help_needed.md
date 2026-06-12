---
title: "Apt-get =&gt; help needed"
date: 2006-06-16
forum: General Help
---

### Post by arnor on 2006-06-16
hi,
i just install ubuntu 606 on my laptop and i got some problems with apt-get.
i just cann't download java or eclipse or totem-xine...there aren't in the list. And when i try in the console i get an error...i also tryed Applications, Add/Delete ... but its written my configuration cann't support these programms... any ideas?
thx 
arnor

Here is my sources.list :
```

deb http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://be.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```

---

### Post by BitTorrentBuddha on 2006-06-16
Could you please post the error you get when running it from a terminal?

---

### Post by arnor on 2006-06-16
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
E: Impossible de trouver le paquet sun-java5-bin

what means he cann't find sun-java5-bin...

---

### Post by allix on 2006-06-16
In Synaptic, go to Settings -> Repositories. Click the "Add" button, then check "universe" and "multiverse" in the dialog. Close it and click Reload in Synaptic. You should see them in the list now.

---

### Post by arnor on 2006-06-16
could anyone send me his sources.list file? please...i changed mine and it works now but i have some error, it was from another computer ;-)
thx
ps: its working now

---

### Post by az on 2006-06-16
[QUOTE=arnor]could anyone send me his sources.list file? please...i changed mine and it works now but i have some error, it was from another computer ;-)
thx
ps: its working now[/QUOTE]
For the record, using synaptic to add repositories actually does change your sources.list.  There is no need to do it by hand.

You can if you want to, of course, but there is no need.

---

