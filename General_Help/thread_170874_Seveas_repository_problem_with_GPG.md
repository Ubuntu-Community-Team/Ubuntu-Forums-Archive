---
title: "Seveas repository problem with GPG"
date: 2006-05-05
forum: General Help
---

### Post by Ronbo on 2006-05-05
I have added the Seveas repositories to my sources.list, when I try to  generate the gpg keys I get the following error.  I have been trying for some time but have had no luck,  I was hoping someone could tell me if I am doing something wrong or if something has changed.  I am running Ubuntu Breezy, below is the error I am recieving.


> 
ron@ubuntu:~$ gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg: requesting key 1135D466 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


Any help would be greatly appreciated.  I am trying to install the FreeNX server.

My sources.list is:

> 
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by jrib on 2006-05-05
try using keyserver.ubuntu.com as the key server

---

### Post by Ronbo on 2006-05-05
[QUOTE=_jason]try using keyserver.ubuntu.com as the key server[/QUOTE]

Still gives me the same error, I don't have a clue why this is.

---

### Post by jrib on 2006-05-05
[http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/)

can you access that in your browser?

---

### Post by Ronbo on 2006-05-05
[QUOTE=_jason][http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/)

can you access that in your browser?[/QUOTE]


Nope no luck accessing it in the browswer either, I get a popup that says:

 'The operation timed out when attempting to contact keyserver.ubuntu.com.'

---

### Post by jrib on 2006-05-06
do you have something blocking that port? firewall, router, isp?

(I actually don't know if this question makes sense)

---

### Post by nanotube on 2006-05-06
[QUOTE=_jason]do you have something blocking that port? firewall, router, isp?

(I actually don't know if this question makes sense)[/QUOTE]
the question makes perfect sense - because i can access keyserver.ubuntu just fine - so it is not a problem on the server side...

---

### Post by Ronbo on 2006-05-08
[QUOTE=nanotube]the question makes perfect sense - because i can access keyserver.ubuntu just fine - so it is not a problem on the server side...[/QUOTE]

I think that was it, I am trying to set it up at work but it must be being blocked at the firewall.  I can access it at home, thanks for the suggestions and the help.

---

### Post by gldvxx on 2007-03-08
is there an alternative way to get the keys for people who are behind a firewall?  i was able to find the keys i needed at [http://keyserver.noreply.org/](http://keyserver.noreply.org/) but i'm not sure exactly how to download them or export them into apt!!

---

