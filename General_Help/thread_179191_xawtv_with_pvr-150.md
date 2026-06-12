---
title: "xawtv with pvr-150"
date: 2006-05-19
forum: General Help
---

### Post by dlai on 2006-05-19
LOOOK AT THIS GUYS!!!!!!! Finally an application that supports mpeg2-encoding cards like pvr-150, pvr-550 and pvr-350. Now you can change channels and watch tv in the same application with good quality!!!! ( I konw I posted this another place, but I have no idea what i've done since I posted in Ubuntu warty live cd forum. DOH!](*,) , so admin please delete, since this is a repost in the correct forum)

Quote:
Getting started and Overview about the changes in xawtv version 4.x
================================================== =================


Changes/Status Overview
-----------------------

New Features + Changes

* MPEG software decoding, and based on that:
- support for DVB cards, including Budget cards.
**- support for MPEG Encoder cards (ivtv).**
* reworked configuration framework.
* switch over to gtk as X11 GUI toolkit.

Dropped Features

* Overlay without Xvideo extention.
* Resolution switching for fullscreen.

Obsolete (likely will be dropped)

* motv application (gtk-ported xawtv will take over

work needed (i.e. broken/untested/incomplete right now)

* movie recording.
* lirc support.
* documentation is outdated.
* fbtv & ttv.

Ok I tried making a deb for all of you! but I'm really not sure it works, can you please try it out.
It is important that you ```
apt-get remove xawtv-plugins pia scantv
``` there might be more I'm not sure. Here is a link to the file: [http://www.imi.aau.dk/~jfur05/xawtv_20060317-1-cvsnodvb-ubuntu1_i386.deb]("http://www.imi.aau.dk/~jfur05/xawtv_20060317-1-cvsnodvb-ubuntu1_i386.deb")

----------------------------------------------------- If the deb doesn't work------------------------------------------------------------

This is what i ended up installing to make it compile.
```
sudo apt-get install libice-dev libsm-dev libxaw-headers libxaw7-dev libxmu-dev libxmu-headers libxpm-dev libxt-dev libxv-dev libxvmc-dev x11proto-video-dev libmad0-dev libmpeg2-4-dev zvbi libzvbi-dev libjpeg62-dev libncurses5-dev automake1.9
```

This is from the xawtv new in 4.x.... the cvs version already have ivtv support , and it is now playing on my dapper-box....
you can download it [here.]("http://dl.bytesex.org/cvs-snapshots/xawtv-20060317-134453.tar.gz")
```
./autogen.sh
./configure --disable-dvb
make
sudo make install
```

---

