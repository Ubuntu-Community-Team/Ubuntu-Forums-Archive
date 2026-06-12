---
title: "synaptic reload problem: sub-process gzip / bzip returned an error code - FIXED!"
date: 2006-06-09
forum: General Help
---

### Post by pellgarlic on 2006-06-09
after doing a clean install of dapper drake, i was having problems with synaptic giving errors when trying to reload package information from the repositories. i had not made any modifications to the sources.list that dapper created during the installation, which was set up to use the "gb.archive.ubuntu.com" repositories.


when i used the "http://archive.ubuntu.com" repositories, i got this error message:

```
http://archive.ubuntu.com/ubuntu/dists/dapper/**main**/source/Sources.gz: Sub-process gzip returned an error code (1)
```

when i used the "http://gb.archive.ubuntu.com" repositories, i got this error message:

```
http://gb.archive.ubuntu.com/ubuntu/dists/dapper/**restricted**/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
```


looking at the detail of the errors, i noticed that using the "gb.archive" repository, gave me a problem with the "Packages.bz2" in "restricted", and using the plain "archive" repository gave me a problem with "Sources.gz" in "Main". (relevant parts marked in **bold**) so, i tried changing my sources.list to use the "gb.archive" repositories for "Main" and not "restricted", and the "archive" repositories for "restricted" and not "main", as follows:

original:

```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
[B]deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted[/B]

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```


modified:

```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
[B]deb http://archive.ubuntu.com/ubuntu/ dapper restricted
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main
deb-src http://archive.ubuntu.com/ubuntu/ dapper restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main[/B]

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates restricted
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

end result: reloading package information works, with no errors! 

i have no idea why these problems are occurring, as when i browse to the archive in firefox, and click on the offending files (Sources.gz or Packages.bz2) they seem to open fine. also, technically, the "gb.archive" and plain "archive" should be the same, so perhaps there is a problem within synaptic itself? 

this fix works for me, although i expect it may not continue to work, and i may have to switch things about again at some point, but i thought it may be of use to some others who are having similar problems. (although each paricular situation will require different combinations of modifications - just take note of your particular error message, and whether the file in question is in the "main" or "restricted", and add and modify lines as required).



[Edit: SECOND METHOD:

having found this thread from last year: [http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error) it appears this problem has been around for some witme. the solution arrived at in that thread, was to change the "http" in the sources.list to "ftp". worth a shot as well. i can't test it myself right now, as i'm at work (my ubuntu pc is at home) but i will try it when i can]

---

### Post by Mark_in_Hollywood on 2006-10-02
Yes, this fixed mine, too. No more gzip sub=process error message. I am adding this to update this thread for others to find it more readily.

After changing the repositories, I was, for a 3rd time in as many days, offered a newer version of Automatix. It was downloaded. I don't know if that will make a difference with the other problems this computer has, no audio streaming, shakey modem connection, but at least ONE problem is solved.

---

