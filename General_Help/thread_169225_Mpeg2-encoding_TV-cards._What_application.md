---
title: "Mpeg2-encoding TV-cards. What application?"
date: 2006-05-02
forum: General Help
---

### Post by dlai on 2006-05-02
Hey everybody
I have recently bought a PVR-150 tv-tuner card, but I'm unable to find any application capableof changing channels and watching tv. Right now I'm using a combination of xaw-tv (for changing channels) and mplayer (for watching tv), which is not a good solution. Does anybody know an application that can do both with ivtv-based cards?

---

### Post by the_tiger on 2006-05-02
You can get a great setup for this card using mythtv. It is a fully featured pvr solution and very flash.

[http://www.quietglow.com/docs/ubuntumythtv.html]("http://www.quietglow.com/docs/ubuntumythtv.html")
[I]
edit: just saw your post in another thread so assume you already know this. Will leave link for others to follow[/I]

---

### Post by dlai on 2006-05-02
yeah sorry i know... and I have already tried mythtv... but it is way too heavy and I don't want all those extra things it can I just want simple TV-watching, sometimes even a small window

---

### Post by Jason_25 on 2006-05-02
Yeah, mythtv rocked my ubuntu system after installing it.  Big mistake.  To just watch tv, tvtime is awesome.

---

### Post by dlai on 2006-05-02
Yes I know them all tvtime, zapping, xawtv, motv and even mplayertv... but none of them have I found to make good use of the mpeg2-encoding cards like my pvr-150 or cards that use ivtv-drivers

---

### Post by the_tiger on 2006-05-02
I agree. There is a big hole in the apps available for tv recording. There should be a simple windowed program for recording from standard tv cards using processor compression let alone from dedicated pvr cards. Such an app would be very welcome.

---

### Post by dlai on 2006-05-02
yes and as I see it should not be that hard to create, since one can combine a simple mpeg-player with a channel-shifter of some sorts (xawtv)... ivtv-tune

---

### Post by dlai on 2006-05-05
LOOOK AT THIS GUYS!!!!!!!

> Getting started and Overview about the changes in xawtv version 4.x
===================================================================


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

   * motv application (gtk-ported xawtv will take over ;)

 work needed (i.e. broken/untested/incomplete right now)

   * movie recording.
   * lirc support.
   * documentation is outdated.
   * fbtv & ttv.

This is from the xawtv new in 4.x.... the cvs version already have ivtv support , and it is reported working!!!!!!! But I just can't make it compile....[here]("http://dl.bytesex.org/cvs-snapshots/xawtv-20060317-134453.tar.gz") is a link to the newest snapshot

---

### Post by dlai on 2006-05-05
wuhuuu i got it working.. not so hard just some -dev .deb's that needed to be installed

---

### Post by Jason_25 on 2006-05-06
Could you give any hints on what you needed to install to compile it?

---

### Post by dlai on 2006-05-06
here are what i ended up installing:
libice-dev (2:1.0.0-0ubuntu2)
libsm-dev (2:1.0.0-0ubuntu2)
libxaw-headers (2:1.0.1-0ubuntu3)
libxaw7-dev (2:1.0.1-0ubuntu3)
libxmu-dev (2:1.0.0-0ubuntu3)
libxmu-headers (2:1.0.0-0ubuntu3)
libxpm-dev (1:3.5.4.2-0ubuntu3)
libxt-dev (1:1.0.0-0ubuntu3)
libxv-dev (2:1.0.1-0ubuntu3)
libxvmc-dev (2:1.0.1-0ubuntu4)
x11proto-video-dev (2.2.2-0ubuntu2)
libmad0-dev (0.15.1b-2.1)
libmpeg2-4-dev (0.4.0b-4ubuntu1)
zvbi (0.2.17-5)
libzvbi-dev (0.2.17-5)
libjpeg62-dev (6b-11)
libncurses5-dev (5.5-1ubuntu3)
automake1.9

---

### Post by Jason_25 on 2006-05-06
Yeah I have all the abve installed and I was getting this.
```

ar: creating libng/libng.a
  LD      console/streamer
  CC      console/webcam.o
  CC      console/ftp.o
  LD      console/webcam
  CC      console/radio.o
  LD      console/radio
  CC      console/v4l-info.o
  CC      structs/struct-v4l.o
  CC      structs/struct-v4l2.o
  LD      console/v4l-info
  CC      console/v4l-conf.o
  LD      console/v4l-conf
  CC      debug/sysfs.o
  LD      debug/sysfs
  CC      debug/xvideo.o
  LD      debug/xvideo
  CC      debug/dvb-signal.o
  LD      debug/dvb-signal
  CC      debug/vbi-rec.o
  LD      debug/vbi-rec
  CC      debug/epg.o
  CC      common/dvb-monitor.o
common/dvb-monitor.c:14:18: error: glib.h: No such file or directory
common/dvb-monitor.c:32: error: syntax error before &#8216;GIOChannel&#8217;
common/dvb-monitor.c:32: warning: no semicolon at end of struct or union
common/dvb-monitor.c:33: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;id&#8217;
common/dvb-monitor.c:33: warning: data definition has no type or storage class
common/dvb-monitor.c:36: error: syntax error before &#8216;}&#8217; token
common/dvb-monitor.c:111: error: syntax error before &#8216;table_data&#8217;
common/dvb-monitor.c:111: error: syntax error before &#8216;*&#8217; token
common/dvb-monitor.c:113: warning: return type defaults to &#8216;int&#8217;
common/dvb-monitor.c:113: warning: no previous prototype for &#8216;table_data&#8217;
common/dvb-monitor.c: In function &#8216;table_data&#8217;:
common/dvb-monitor.c:114: error: &#8216;data&#8217; undeclared (first use in this function)
common/dvb-monitor.c:114: error: (Each undeclared identifier is reported only once
common/dvb-monitor.c:114: error: for each function it appears in.)
common/dvb-monitor.c:123: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:124: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:124: error: &#8216;source&#8217; undeclared (first use in this function)
common/dvb-monitor.c:130: error: &#8216;FALSE&#8217; undeclared (first use in this function)common/dvb-monitor.c:134: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:137: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:137: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:139: error: &#8216;TRUE&#8217; undeclared (first use in this function)
common/dvb-monitor.c:141: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:150: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:151: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:154: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:178: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_find&#8217;:
common/dvb-monitor.c:226: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:227: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:227: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_open&#8217;:
common/dvb-monitor.c:235: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:238: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:238: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:238: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:239: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:240: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:244: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:244: warning: implicit declaration of function &#8216;g_io_channel_unix_new&#8217;
common/dvb-monitor.c:244: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:245: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:245: warning: implicit declaration of function &#8216;g_io_add_watch&#8217;
common/dvb-monitor.c:245: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:245: error: &#8216;G_IO_IN&#8217; undeclared (first use in this function)
common/dvb-monitor.c:248: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:248: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:248: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_close&#8217;:
common/dvb-monitor.c:253: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:256: warning: implicit declaration of function &#8216;g_source_remove&#8217;
common/dvb-monitor.c:256: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:257: warning: implicit declaration of function &#8216;g_io_channel_unref&#8217;
common/dvb-monitor.c:257: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:258: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:259: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:260: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:261: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:262: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:263: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:268: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:268: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_next&#8217;:
common/dvb-monitor.c:277: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:278: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:280: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_add&#8217;:
common/dvb-monitor.c:296: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:297: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:298: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:299: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:300: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:301: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:302: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:303: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:304: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:307: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:307: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:307: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:307: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_del&#8217;:
common/dvb-monitor.c:322: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:322: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:323: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;table_refresh&#8217;:
common/dvb-monitor.c:329: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:329: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:329: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:330: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:331: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:333: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:334: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:335: error: dereferencing pointer to incomplete type
common/dvb-monitor.c: In function &#8216;dvbmon_fini&#8217;:
common/dvb-monitor.c:386: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:387: error: dereferencing pointer to incomplete type
common/dvb-monitor.c:387: error: dereferencing pointer to incomplete type
make: *** [common/dvb-monitor.o] Error 1

```
Since I don't have a DVB anything, I fixed it by disabling DVB in the configure script.
```

./configure --disable-dvb

```
Even so, the make seems to stop suddenly without an error code like this
```

In file included from x11/rootv.c:27:
./jwz/vroot.h: In function &#8216;VirtualRootWindowOfScreen&#8217;:
./jwz/vroot.h:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
  LD      x11/rootv
msgfmt -o po/cs.mo po/cs.po
msgfmt -o po/de.mo po/de.po
msgfmt -o po/pl.mo po/pl.po
msgfmt -o po/ru.mo po/ru.po

```
The xawtv executable does not get built this way.  Only a few of it's files do unfortnately.

---

### Post by dlai on 2006-05-06
And you have everything working...? I mean you can play your card with mplayer /dev/video0? Do you have your graphics card working? I don't know what is wrong... maybe you should to try out the cvs version...

---

### Post by Jason_25 on 2006-05-06
Yeah, video acceleration is working.  I can also view tv with tvtime and view and record with XDTV.  I've used the command line utilities from the 3.x versions before to change contrast and such from and command line but I wanted to see what the graphical side of this program, especially 4.x, was all about.  Maybe I will try the CVS version.

---

### Post by dlai on 2006-05-07
But then you must have another card than ivtv-based card... and by that i would say that you would not need xawtv in the newest version... but again it might have some functionalities that you can use... i don't know

---

### Post by dlai on 2006-05-14
i have started a new thread with a howto that explains... some of the install of xawtv...
[XAWTV]("http://www.ubuntuforums.org/showthread.php?t=170884")

---

