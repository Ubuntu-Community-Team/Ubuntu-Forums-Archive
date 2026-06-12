---
title: "updates error"
date: 2009-11-10
forum: General Help
---

### Post by Achilles124 on 2009-11-10
When i want to check if I have any updates, I run the update window, and then i get the following eror:

> Ophalen van //azores.linex.org/gambas-other/dists/gutsy/Release.gpg[/url]  is mislukt
Ophalen van azores.linex.org/gambas-other/dists/gutsy/main/i18n/Translation-nl.bz2[/url] is mislukt
Ophalen van //nl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz[/url] 404  Not Found [IP: 213.136.29.211 80] is mislukt
Ophalen van //security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz[/url] 404  Not Found is mislukt
Ophalen van //security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz[/url] 404  Not Found is mislukt

How is it possible that Ubuntu still wants to get updates for gutsy?
(btw: "is mislukt" means failed).

How can I solve this?

---

### Post by dvlchd3 on 2009-11-10
Are you connected to the Internet?  Can you ping the repo?

```

ping nl.archive.ubuntu.com
ping security.ubuntu.com

```

---

### Post by Achilles124 on 2009-11-10
> PING ubuntuarchive.bit.nl (213.136.29.211) 56(84) bytes of data.
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=2 ttl=58 time=11.0 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=3 ttl=58 time=11.3 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=4 ttl=58 time=10.7 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=6 ttl=58 time=10.5 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=7 ttl=58 time=10.5 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=8 ttl=58 time=10.4 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=9 ttl=58 time=10.7 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=11 ttl=58 time=10.3 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=12 ttl=58 time=10.7 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=13 ttl=58 time=10.9 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=14 ttl=58 time=10.2 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=15 ttl=58 time=10.7 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=16 ttl=58 time=12.4 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=17 ttl=58 time=11.2 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=18 ttl=58 time=10.9 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=19 ttl=58 time=10.2 ms
64 bytes from ubuntuarchive.bit.nl (213.136.29.211): icmp_seq=20 ttl=58 time=11.1 ms


This is what I get.

---

### Post by Achilles124 on 2009-11-10
> ecmpeek@ecmpeek-desktop:~$ ping security.ubuntu.com
PING security.ubuntu.com (91.189.88.37) 56(84) bytes of data.
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=1 ttl=55 time=18.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=2 ttl=55 time=17.4 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=3 ttl=55 time=17.0 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=4 ttl=55 time=17.9 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=5 ttl=55 time=17.0 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=6 ttl=55 time=17.6 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=7 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=8 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=9 ttl=55 time=17.4 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=10 ttl=55 time=17.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=11 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=12 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=13 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=14 ttl=55 time=17.0 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=15 ttl=55 time=16.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=16 ttl=55 time=17.4 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=17 ttl=55 time=18.0 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=18 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=19 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=20 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=21 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=22 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=23 ttl=55 time=16.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=24 ttl=55 time=17.1 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=25 ttl=55 time=17.6 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=26 ttl=55 time=17.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=27 ttl=55 time=17.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=28 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=29 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=30 ttl=55 time=17.2 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=31 ttl=55 time=16.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=32 ttl=55 time=17.4 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=33 ttl=55 time=17.6 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=34 ttl=55 time=16.7 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=35 ttl=55 time=17.2 ms


And this is what I get for ping security.ubuntu.com
So I guess that is allright.

---

### Post by DroopZ on 2009-11-10
Which version of Ubuntu are you running now ?

---

### Post by Achilles124 on 2009-11-10
The latest: karmic

---

### Post by DroopZ on 2009-11-10
Try this:

Rename your **/etc/apt/sources.list** file and create a new one with the following content:
(replace the "de" servers with the "nl" servers if you like, but this should work.)

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-security multiverse
```

---

### Post by Achilles124 on 2009-11-10
The etc/apt/ file is a complete mess:

Here are some files that can be found there:
apt.conf.d     
source.list.akiradbackup  
sources.list.distUpgrade  
trusted.gpg
preferences.d  
sources.list              
sources.list.save         
trusted.gpg~
secring.gpg    
sources.list.d            
trustdb.gpg

I will try to change the sources.list file but this is not normal, is it?

---

### Post by DroopZ on 2009-11-10
Looks about the same on my PC.

I think these files get renamed when you perform a distribution upgrade.

Don't worry about it.

---

### Post by Achilles124 on 2009-11-10
Okay, worked. Thank you, Droopz. :KS

---

