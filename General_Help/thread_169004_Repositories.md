---
title: "Repositories?"
date: 2006-05-01
forum: General Help
---

### Post by Leon945 on 2006-05-01
Hi All!
I was tryin to update the packages on the synaptic package manager.. and i got like 16 of errors just like this one:

[B]W: Couldn't stat source package list [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
[/B]

Have the repositories changed? or what's going on?

---

### Post by Ramses de Norre on 2006-05-01
Still not working? If so can you post your sources.list? The server is working for me..

---

### Post by Leon945 on 2006-05-01
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

---

### Post by PhoenixP3K on 2006-05-02
I've checked [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) and the link seems to be working. I mean it happens from time to time for a server to be down. I found that this happens more often with "mirrors" or regional repositories, like ca.archives.ubuntu.com or others.

---

### Post by nanotube on 2006-05-02
when you get those "couldnt stat" errors, have you tried just hitting the "reload" button in synaptic? that should make it update the listings, if the servers are up.

---

### Post by Cannon Fodder on 2006-05-02
Personally I find the synaptic package manager extremely complicated to find anything on. The names are so freaking cryptic. I have similar problems to leon.That and I can't seem to install half of the shit I'm trying to install.

---

### Post by aysiu on 2006-05-02
[QUOTE=Cannon Fodder]Personally I find the synaptic package manager extremely complicated to find anything on. The names are so freaking cryptic. I have similar problems to leon.That and I can't seem to install half of the shit I'm trying to install.[/QUOTE] Try searching by name and description instead of by name.

---

### Post by deadgobby on 2006-05-02
Have your check this link
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
Hope this helps
Gobby

---

### Post by Leon945 on 2006-05-02
OK!
I think a server was down or something.. it seems to be working now.. thanks people!

By the way Cannon Foder, I think the same as you.. hehe.. but i guess it works from time to time..

---

