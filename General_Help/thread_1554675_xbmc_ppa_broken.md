---
title: "xbmc ppa broken?"
date: 2010-08-17
forum: General Help
---

### Post by bprins on 2010-08-17
Hi,

I can't install XBMC from its repositories. Followed the xbmc step by step, added repo without errors, but xbmc doesnt pop up when tabbing:

```

sudo apt-get install xb[tab][tab]

bas@ubuntu-laptop:~$ sudo apt-get install xb
xbacklight         xbiff              xblast-tnt-images  xboing
xball              xbill              xblast-tnt-levels  xbomb
xbanner            xbindkeys          xblast-tnt-mini    xbs
xbase              xbindkeys-config   xblast-tnt-models  xbubble
xbase-clients      xbitmaps           xblast-tnt-musics  xbubble-data
xbatt              xbl                xblast-tnt-sounds  xbuffy
xbattbar           xblast             xbmc-ppa-keyring   
xbattle            xblast-tnt         xboard             

```

All I get is the ppa-keyring from XBMC.

What's going on? Nothing on xbmc site either.

Thanks.

Bas

---

### Post by mhgsys on 2010-08-17
yes; the ppa is broken indeed.

instead of sudo add-apt-repository ppa:team-xbmc
use;
```
sudo add-apt-repository ppa:team-xbmc-svn/ppa
```
followed by a
```
sudo apt-get update
```

after doing that;

xbmc will install fine.


> mhg@mhg-desktop:~$ sudo apt-get install xbmc xbmc-standalone
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
libass4 libfaad2 libglew1.5 libmad0 libmicrohttpd5 libmikmod2 libmms0
libmng1 libmodplug0c2 libmpeg2-4 libpcrecpp0 libqt3-mt librtmp0
libsdl-image1.2 libsdl-mixer1.2 libsmpeg0 libvdpau1 python-qt3 python-sip
xbmc-bin xbmc-data xbmc-skin-confluence xbmc-web
Suggested packages:
glew-utils libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc nvidia-vdpau-driver
vdpau-driver python-qt3-gl python-qt3-doc xbmc-third-parties
xbmc-test-helper
The following NEW packages will be installed:
libass4 libfaad2 libglew1.5 libmad0 libmicrohttpd5 libmikmod2 libmms0
libmng1 libmodplug0c2 libmpeg2-4 libpcrecpp0 libqt3-mt librtmp0
libsdl-image1.2 libsdl-mixer1.2 libsmpeg0 libvdpau1 python-qt3 python-sip
xbmc xbmc-bin xbmc-data xbmc-skin-confluence xbmc-standalone xbmc-web
0 upgraded, 25 newly installed, 0 to remove and 11 not upgraded.
Need to get 44.5MB of archives.
After this operation, 100MB of additional disk space will be used.
Do you want to continue [Y/n]? 

---

### Post by bprins on 2010-08-17
Nope, done that already but also that repo doesn't have the xbmc packages.

Any other advice?

Can you see which repo holds the Xbmc package? Maybe you have another repo that presents the Xbmc packages? (unlikely, I know, but I'm sure the 2 added repo's don't give me Xbmc)

Thank a lot in advance!

bas

---

### Post by MockY on 2010-08-17
None of those two ppas works for me either. I get E: Couldn't find package xbmc regardless of ppa I add. And it does not matter how many times I update just in case that would make a difference).

---

### Post by MockY on 2010-08-17
It's all down. And it seems like it's been down for a while. And all this without a single announcement...in my mind, that is bad.

Anyhow, more info can be found here
[http://forum.xbmc.org/showthread.php?t=79143](http://forum.xbmc.org/showthread.php?t=79143)

---

### Post by stinkeye on 2010-08-17
I downloaded and installed yesterday from the live cd and its working.
[**_[COLOR="DarkRed"]http://xbmc.org/download/[/COLOR]_**]("http://xbmc.org/download/")

---

