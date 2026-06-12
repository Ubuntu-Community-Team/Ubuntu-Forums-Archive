---
title: "Missing plugin - Windows Media Speech Decoder?"
date: 2009-10-27
forum: General Help
---

### Post by x C0MMAND0 x on 2009-10-27
I tried to watch [this video]("http://www.ar.cc.mn.us/saari/engr2241/exam2_review-1.wmv") as a review for engineering.  When I tried to play it, I got the following error:

Missing Plugin
"Windows Media Speech Decoder" (see attached image).

I tried:
VLC
Realplayer
mplayer
totem

No luck.  Any ideas?

---

### Post by phillw on 2009-10-27
Best I can spot is .....

[http://ubuntuforums.org/archive/index.php/t-639393.html](http://ubuntuforums.org/archive/index.php/t-639393.html)

Okay, so it's a pain to fork out money, but they are propriatory codecs..

The people on that thread seem to think it's worth the money.

Hope that is of help,

Regards,

Phill.

---

### Post by x C0MMAND0 x on 2009-10-28
I can't believe the only way to get it to work is to pay for plug-ins...

---

### Post by mbeach on 2009-10-28
I haven't tried it, but it seems quite similar to:
[http://ubuntuforums.org/showthread.php?t=1024820](http://ubuntuforums.org/showthread.php?t=1024820)

specifically the part about the medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

even more specifically, you might just need to do:
```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb
sudo dpkg -i w32codecs_20071007-0medibuntu2.1_i386.deb

```

Then play your video with mplayer.

---

### Post by andrew.46 on 2009-10-28
Hi COMMANDO,

> **x C0MMAND0 x said:**
> I tried to watch [this video]("http://www.ar.cc.mn.us/saari/engr2241/exam2_review-1.wmv") as a review for engineering.

Looks like MPlayer will play this file by using external codecs. For Ubuntu you would need to install the MEdibuntu w32codecs pack. If you are running the 64bit MPlayer you will be in a bit of trouble :(. I attach a screenshot of this file playing successfully under the svn MPlayer.

Andrew

---

### Post by x C0MMAND0 x on 2009-10-29
I can get the video to play, but there is no audio using mplayer, and yes, I am using a 64bit os.

---

### Post by andrew.46 on 2009-10-29
Hi Commando,

> **x C0MMAND0 x said:**
> I can get the video to play, but there is no audio using mplayer, and yes, I am using a 64bit os.

Unfortunately the *w64codecs* will not help you I'm afraid as there are only 2 or 3 codecs there. You really need the 32bit MPlayer + w32codecs for this stream and although this can be loaded onto a 64bit system I lack the expertise to demonstrate how to do that.

Andrew

---

### Post by mc4man on 2009-10-29
It's not too difficult to build and install a 32 bit mplayer, I'm sure there are some threads about it. I did it on a jaunty live cd to see what's involved. I think there's a post about what I found a few months ago. ( could retrieve if you're going to try.

This app makes it a bit easier to do
[http://ubuntuforums.org/showthread.php?t=474790&highlight=32+bit+mplayer](http://ubuntuforums.org/showthread.php?t=474790&highlight=32+bit+mplayer)

While not nearly as useful as a real build/install you can  use a 32 bit mplayer windows build in wine (wine is 32 bit

The trick is to get a binary that doesn't need to be installed, just unpacked and run.
While it could be possible to use a build that uses an installer, odds are problems will arise.

The main limitation is that in the example I'll link to the mplayer build is gui only, but again running a command line app in wine takes some doing, if at all.

This build is a bit dated but works perfectly to play your video, there may be newer ones that satisfy the main requirement (no install

see here post # 40
[http://ubuntuforums.org/showthread.php?t=848535&highlight=32%2Bbit%2Bmplayer&page=4](http://ubuntuforums.org/showthread.php?t=848535&highlight=32%2Bbit%2Bmplayer&page=4)

The script is just a bunch of commands that can be run separately, shown here
```


sudo apt-get install wine

wget -c ftp://ftp4.mplayerhq.hu/MPlayer/releases/win32/MPlayer-1.0rc2-gui.zip
unzip MPlayer-1.0rc2-gui.zip

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007.orig.tar.gz 
tar zxvf w32codecs_20071007.orig.tar.gz
mv ./all-20071007/* ./MPlayer-1.0rc2-gui/codecs
rmdir all-20071007
 
```


Audio needs to be configured in wine, for jaunty the default choice of alsa should work, for karmic alsa should be unchecked and oss enabled ( otherwise a puleaudio patched wine is needed.

screen shows the win32 gui with your url in playback (worked fine

---

