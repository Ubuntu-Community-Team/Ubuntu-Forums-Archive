---
title: "can't install flash"
date: 2006-05-14
forum: General Help
---

### Post by IsKall on 2006-05-14
why do I get this error? When I type   sudo apt-get install flashplayer-mozilla

```
E: Couldn't find package flashplayer-mozilla
```

and I have the universe repositories enabled.

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
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe



deb http://wine.sourceforge.net/apt/ binary/


```

Anyone who can help me? Really wants to flash work. I tried from the synaptic to find it and tried to install nonfree version but that didn't work either.

---

### Post by Sef on 2006-05-14
you need to install multiverse after universe.

here:  ```
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe
```

it should look like this:

```
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe multiverse 
```

---

### Post by IsKall on 2006-05-14
install? I just added the last line. But it still doesn't work, apt-get can't find it.

---

### Post by IsKall on 2006-05-14
anyone?

---

### Post by cjazz on 2006-05-14
Actually your added lines probably should look like this:

```
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse 
```

And make sure to do this afterward:

```
sudo apt-get update
```

---

### Post by _aeon on 2006-05-14
Why not trying install manually?

1.- Download [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")
2.- Copy (as root) the following files to your browser's plugins folder (normally this is /usr/lib/firefox/plugins): 

- libflashplayer.so 
- flashplayer.xpt 

3.- Restart Firefox.
4.- Tada!

---

### Post by IsKall on 2006-05-15
thank you _aeon, your help worked! Needed to copy those files. A bit stupid installation, the installation of flash should already have fixed that part too :S

well thanks for the help anyway. :)

---

