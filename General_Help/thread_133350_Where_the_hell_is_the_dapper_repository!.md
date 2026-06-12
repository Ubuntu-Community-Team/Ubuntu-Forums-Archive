---
title: "Where the hell is the dapper repository!"
date: 2006-02-20
forum: General Help
---

### Post by electricpainter on 2006-02-20
Can somebody please give me a link to a dapper repository that contains xgl packages? I've been searching for it or one of them. I don't even know if it's a type of repository.

Completely Confused,
ElectricPainter

---

### Post by r4ik on 2006-02-20
There is a howto on xgl,

[http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)

Good  luck !
There is more on the subject here,

[http://www.ubuntuforums.org/forumdisplay.php?f=111](http://www.ubuntuforums.org/forumdisplay.php?f=111)

---

### Post by electricpainter on 2006-02-20
i've already been to that page. it only tells me to go to the dapper universe repository to get the packages. but it fails to give me a link to such repository.

---

### Post by codejunkie on 2006-02-20
[QUOTE=electricpainter]i've already been to that page. it only tells me to go to the dapper universe repository to get the packages. but it fails to give me a link to such repository.[/QUOTE]
run ```
sudo gedit /etc/apt/sources.list
``` and make your sources.list file look like this 
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

```
save the file and run ```
sudo apt-get update
``` to refresh the sources.

---

