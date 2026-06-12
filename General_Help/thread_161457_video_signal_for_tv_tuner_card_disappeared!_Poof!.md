---
title: "video signal for tv tuner card disappeared! Poof!"
date: 2006-04-17
forum: General Help
---

### Post by bdmp on 2006-04-17
Ok I installed a kworld pvr 7130 tv tuner card and it was working fine and then the screen went black. I was trying to add channels to xawtv settings when it happend. I restarted, reloaded the driver, removed (--purge) xawtv and reinstalled, and a number of  other  things.

I think it is not xawtv  because I get no video in tvtime too.

The sound works fine.

Below is a bunch of important info about my card. Hope it helps.

Please help me fix this.


First here is some info on my card:
[http://paste.ubuntu-nl.org/12376](http://paste.ubuntu-nl.org/12376)

Here is what I did to get the card to work:
 ```
 sudo modprobe saa7134 card=3 tuner=2

```
Basically, for "card=" any number seemed to be fine except 5. For the "tuner=" ntsc is 2 and the card has "ntsc" checked on the front and I live in Japan which uses "ntsc".

dmesg says
```
31.
      [4296329.640000] tuner 0-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
``` which is good so we know that "tuner=2" for NTSC, right?

The strange thing about this is that it says
 ```
 28.
      [4296329.455000] saa7130[0]: subsystem: 1131:0000, board: SKNet Monster TV [card=5,insmod option]
``` this is strange because if I change "card=5" it does not work. So maybe that is incorrect information?

Here is my full dmesg output:
[http://kubuntu.pastebin.com/663221](http://kubuntu.pastebin.com/663221)

Ok, now here is some info I have found on the net:

Here is a page with someone trying to install my card on kubuntu. One major difference is the "tuner=" setting. Mine is NTSC and his is PAL or something.  Here it is:
[http://www.flexbeta.net/forums/lofiversion/index.php/t7604.html](http://www.flexbeta.net/forums/lofiversion/index.php/t7604.html)

So I am about to buy a tv if this doesn't work soon. Save me 10000 yen and tell me how to fix this please :)

---

### Post by bdmp on 2006-04-17
This is what I get when I run xawtv from the command line. I wonder if  it helps.

```
burepe@gochagocha:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.12-9-386)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
v4l2: read: Input/output error
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Input/output error
v4l2: read: Input/output error
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Input/output error
v4l2: read: Input/output error

```

---

### Post by bdmp on 2006-04-19
I fixed the problem by uninstalling (purge) all the tv related programs and reinstalling. I still don't know what caused it though.

---

