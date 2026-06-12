---
title: "gunzip"
date: 2006-05-19
forum: General Help
---

### Post by IsKall on 2006-05-19
Need help to install gtar, did this command: sudo apt-get install gtar, but got this error:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtar

Here is my repositorie:


```

# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

deb-src http://se.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
## deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe
## deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

## deb http://security.ubuntu.com/ubuntu dapper-security main restricted
## deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
## deb http://security.ubuntu.com/ubuntu dapper-security universe
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe



## deb http://wine.sourceforge.net/apt/binary/

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse 

```

---

### Post by Steven_B on 2006-05-19
I don't see gtar in the repositories anywhere.  If you need to zip and unzip things, use archive manager.  You can also use "zip", "unzip", "gzip", "gunzip", and "tar" at the command line.

---

### Post by nudaz on 2006-06-29
[QUOTE=Steven_B]I don't see gtar in the repositories anywhere.  If you need to zip and unzip things, use archive manager.  You can also use "zip", "unzip", "gzip", "gunzip", and "tar" at the command line.[/QUOTE]
 I have 6.06 server and couldn't find a way to unzip a file,
tried
unzip - command not found
gunzip - couldn't unzip a zip file
tar - didn't work either
so how do you unzip at the command line if unzip isn't an available command?
(apt-get couldn't find it either)

---

### Post by ifokkema on 2006-07-01
[QUOTE=nudaz]I have 6.06 server and couldn't find a way to unzip a file,
tried
unzip - command not found
gunzip - couldn't unzip a zip file
tar - didn't work either
so how do you unzip at the command line if unzip isn't an available command?
(apt-get couldn't find it either)[/QUOTE]
```
sudo apt-get install unzip
unzip <file>
```
will do the trick for you...

---

