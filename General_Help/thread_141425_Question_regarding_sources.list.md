---
title: "Question regarding sources.list"
date: 2006-03-08
forum: General Help
---

### Post by henriette_holm on 2006-03-08
Hi.
It's been a (very) long time since I've looked at the sources.list file last and now I'm wondering: What's the file suppose to look like nowadays if I want to be able to download all the nice stuff (codecs, new versions of programs etc.)? Is there still such a thing as Backports, or?

-Henriette

---

### Post by Lord Illidan on 2006-03-08
Did you enable the extra repos when you first installed Ubuntu?

The sources.list isn't going to change, unless you want to upgrade through Dapper.

If you want, post your sources.list here, so we can point out things which might need changing.

---

### Post by lamego on 2006-03-08
This is a default Breezy sources.list (with universe, multiverse and backports enabled).


```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main
restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://pt.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://pt.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://pt.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://pt.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://pt.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://pt.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://pt.archive.ubuntu.com/ubuntu breezy-backports main restricted univer
se multiverse
 deb-src http://pt.archive.ubuntu.com/ubuntu breezy-backports main restricted un
iverse multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Video codecs and alike are not on some countries so they are not included as default, look at the Automatix script which adds and install most of this "may-not-be-legal" software.

---

### Post by frodon on 2006-03-08
You should read this thread, there's a lot of useful infos in : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by henriette_holm on 2006-03-09
Thanks for posting the file and the link to the other thread - just what I was looking for.

-Henriette

---

