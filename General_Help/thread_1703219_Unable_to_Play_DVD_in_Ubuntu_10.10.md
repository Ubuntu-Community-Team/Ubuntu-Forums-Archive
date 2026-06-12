---
title: "Unable to Play DVD in Ubuntu 10.10"
date: 2011-03-09
forum: General Help
---

### Post by kingbah on 2011-03-09
I am new to Ubuntu and I am unable to play DVDs. I have installed different media players: Gnome, VLC but still no luck. I am wondering if there is something I need to do. Help please.

---

### Post by mastablasta on 2011-03-09
you need to add a package called libdvdcss2. 
 
read more here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
and here: [https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)

---

### Post by nomko on 2011-03-09
[SIZE=1]Open synaptic (System > Administration > Synaptic packagemanager) and search for ubuntu restricted. You have to install this.[/SIZE]
 
[SIZE=1]Then open a terminal and copy/paste this:[/SIZE]
[SIZE=1]```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list [http://www.medibuntu.org/sources.list.d/$(lsb_release](http://www.medibuntu.org/sources.list.d/$(lsb_release) -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```[/SIZE]
 
[SIZE=1]Then search in synaptic for w32codecs and non-free-codecs. If you have a 64-bit system, then use the w64codecs. Install these.[/SIZE]
 
[SIZE=1]Then open a terminal and copy/paste this:[/SIZE]
[SIZE=1]```
sudo /usr/share/doc/libdvdread4/install-css.sh
```[/SIZE]
[SIZE=1]This should do the trick.[/SIZE]

---

### Post by handy on 2011-03-09
Here is some more info' about your situation kingbah:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

