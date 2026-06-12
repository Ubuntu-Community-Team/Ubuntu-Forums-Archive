---
title: "how to get w32 codecs"
date: 2006-03-11
forum: General Help
---

### Post by kittycatsexycat on 2006-03-11
can some one tell me how to get w32 codecs... 

does it include mp3 format....

My synaptic doesn't show alot of packages....e.g lame, games, etc

---

### Post by closeyourwindows on 2006-03-11
[http://ubuntuforums.org/showthread.php?t=138405]("http://ubuntuforums.org/showthread.php?t=138405")
read this thread and install automatix.
there are other ways to get it but this is by far the easiest.

---

### Post by SavageBeginner on 2006-03-11
You could try this guide:  [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by kittycatsexycat on 2006-03-11
nice one dude... thats genius.... hope that gets posted everywhere... especially newbies....

---

### Post by codejunkie on 2006-03-11
[QUOTE=kittycatsexycat]can some one tell me how to get w32 codecs... 

does it include mp3 format....

My synaptic doesn't show alot of packages....e.g lame, games, etc[/QUOTE]

if your wanting mp3 playback installing the w32codecs pack won't help, you need to install gstreamer0.8-plugins & gstreamer0.8-plugins-multiverse packages but first you need to edit your sources.list file and add the multiverse and universe repos, you can do that by running ```
sudo gedit /etc/apt/sources.list
```and make it look like this,
```

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy multiverse

deb http://security.ubuntu.com/ubuntu breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

```
run ```
sudo apt-get update
```then 
```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse
```
then run ```
sudo gst-register-0.8
```

---

### Post by kittycatsexycat on 2006-03-12
Cool, i'll try that after i've installed this automatix thing...

I remember having to do that with the source code last time....

cheers:)

---

