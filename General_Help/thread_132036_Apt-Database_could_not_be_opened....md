---
title: "Apt-Database could not be opened..."
date: 2006-02-17
forum: General Help
---

### Post by flummoxed on 2006-02-17
I very recently installed KDE on a Gnome Ubuntu install. I was using Adept package manager to get some programs, and I accidentally hit the "commit changes" or whatever button when there was nothing to commit. The program crashed, and now whenever I try to open it it gives me this: 

The APT Database could not be opened! This may be caused by incorrect APT configuration or something similar. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

I tried apt-get update, and it gives me this: E: Malformed line 37 in source list /etc/apt/sources.list (dist parse)

When I run apt-setup, it tells me it wants the ubuntu CD in the CD rom drive, but it can't find a CD rom drive. So I try a bunch of paths, /media, hdc/media, dev/media or whatever, and none of them work.

I also tried the good old rule of restarting, and everything will be fine. It's still not working.

What gives?

---

### Post by Lord Illidan on 2006-02-17
Give us your /etc/apt/sources.list

Just type in a terminal:

```
sudo kwrite /etc/apt/sources.list
``` and paste the file here.. you might have a corrupted file.

---

### Post by flummoxed on 2006-02-17
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


deb-src http://archive.ubuntu.com/ubuntu breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe main restricted multiverse 
deb-src http://archive.ubuntu.com/ubuntu breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

# deb http://security.ubuntu.com/ubuntu breezy-security universe 
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

deb http://wine.sourceforge.net/apt/ binary/ 

```

---

### Post by flummoxed on 2006-02-17
Wow, just by looking at that and changing it myself, I got it working again. I added another # to 

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

