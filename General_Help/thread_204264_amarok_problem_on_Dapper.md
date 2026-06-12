---
title: "amarok problem on Dapper"
date: 2006-06-26
forum: General Help
---

### Post by BlacKsheep88 on 2006-06-26
I can't get amarok to play any media file. Every other media player works fine and I have all gstreamer0.10 plugins installed. I can't select gstreamer as an engine, only xine, and I can't find any plugins for xine mp3 support.

---

### Post by mlind on 2006-06-26
I guess the package you're looking for is called libxine-extracodecs
amaroK that's availabe for Dapper supports only xine backend, not gstreamer.

---

### Post by Jucato on 2006-06-26
Yes, *libxine-extracodecs* will do it for you.
You have to enable the multiverse repository first in order to find and install it.

---

### Post by BlacKsheep88 on 2006-06-27
Thanks, that fixed it.

---

### Post by T*&amp;1p87)v# on 2006-06-28
Hi,

I also kind-a have the same problem, but I cannot find the libxine-extracodecs package. Here is my source.list


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Ramses de Norre on 2006-06-28
```
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe
```

Add multiverse to each of these two lines, you only got multiverse on the backports repos now.

---

### Post by T*&amp;1p87)v# on 2006-06-28
10x

thanks a lot for the hint. Everything is fine now, just have to get this xgl working :)

---

