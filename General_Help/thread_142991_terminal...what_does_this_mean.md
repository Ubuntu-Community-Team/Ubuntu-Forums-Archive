---
title: "terminal...what does this mean?"
date: 2006-03-11
forum: General Help
---

### Post by styven on 2006-03-11
Hi all,

I keep getting this when i do anything in a terminal....

styven@edubuntu:~$ apt-cache search libdvdcss
gxine - the xine video player, GTK+/Gnome user interface
ogle - DVD player with support for DVD menus
ogle-mmx - DVD player with support for DVD menus
libdvdread3 - Simple foundation for reading DVDs
libdvdread3-dev - Simple foundation for reading DVDs
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
styven@edubuntu:~$

Any ideas?

---

### Post by bluevoodoo1 on 2006-03-11
Seems like your CDrom is still on your /etc/apt/sources.list . Might want to open up ```
sudo gedit /etc/apt/sources.list
``` and comment out (#) the line containing your CDrom and then run ```
sudo apt-get update
```

---

### Post by styven on 2006-03-11
Hi,

Thanks for you response, i'll keep hold of that command, never seen the source list!

Right, this is my source list..............

deb cdrom:[Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

I can see the cdrom line, it is not prfixed by # or ##, should it be, I am thinking it should be # if i have read your response right.

Steve

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=styven]I can see the cdrom line, it is not prfixed by # or ##, should it be, I am thinking it should be # if i have read your response right.[/QUOTE]

Exactly! Add # in front of the 'deb cdrom' line. After run 

sudo apt-get update

so synaptic will read your newly updated sources.list

---

### Post by styven on 2006-03-11
that's sorted that out, thank you very much!!

---

