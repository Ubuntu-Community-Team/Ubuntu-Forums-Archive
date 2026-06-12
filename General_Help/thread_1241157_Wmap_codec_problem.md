---
title: "Wmap codec problem"
date: 2009-08-15
forum: General Help
---

### Post by fatigue on 2009-08-15
[COLOR=#000000]VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.[/COLOR]
[COLOR=#000000][/COLOR]

[COLOR=#000000]I get this error message when I play .wmv files.[/COLOR]

[COLOR=#000000]so i install [/COLOR]&#8220;*gstreamer0.10-pitfdll*&#8221; and other totem gstreamer codecs.

and I can play most of wmv, still some of wmv, i get those message. 


Anyone has solution for this?

---

### Post by Gipsy25 on 2009-08-15
I am having the same problem ... i am using ubuntu 9.04 I get an error message .. stating that vlc cant play wmv files:

> No suitable decoder module:
VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.

Any work around it ??
Thanks in advance

---

### Post by fatigue on 2009-08-16
anyone please?

---

### Post by mc4man on 2009-08-16
A bit to late here tonight to go into, so just the main info concerning wma and vlc

vlc 0.9.x and 1.x.x can play all wma except mss2 (microsoft screen codec

wma2 is decoded with avcodec so if your version of libavcodecxx supports wma2 so will vlc, any version

wmap,wmal  and wmas are all decoded by dmo (win(w)32codecs if vlc is built with --enable-loader

No repo or ppa versions I've seen enable this option so your out of luck unless you build your own vlc

In 0.9.x the loader (dmo) works perfectly
In 1.x.x it's semi broken, but playback of wmap and wmal is possible with some limitations. (( wma3 is possible with no limitations if decoding is switched to avcodec and a wmapro enabled libavcodecxx is installed

small snippets to show using 0.9.9a in hardy

wma2
> [00000425] asf demux debug: added new audio stream(codec:0x161,ID:1)
[00000427] avcodec decoder debug: ffmpeg codec (Windows Media Audio 2) started
[00000427] main decoder debug: using decoder module "avcodec"

wma3
> [00000425] asf demux debug: added new audio stream(codec:0x162,ID:1)
[00000424] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9.1 Professional" description:"384 kbps, 48 kHz, 2 channel 24 bit 2-pass VBR" information_length:2
[00000427] dmo decoder debug: DMO codec for wmap may work with dll=wma9dmod.dll
[00000427] main decoder debug: using decoder module "dmo"

wmal
> [00000425] asf demux debug: added new audio stream(codec:0x163,ID:1)
[00000424] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9 Lossless" description:"VBR Quality 100, 44 kHz, 2 channel 16 bit 1-pass VBR" information_length:2
[00000427] dmo decoder debug: DMO codec for wmal may work with dll=wma9dmod.dll
[00000427] main decoder debug: using decoder module "dmo"



wmas
> [00000424] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9 Voice" description:" 16 kbps, 16 kHz, mono" information_length:2
[00000425] asf demux debug: added new audio stream(codec:0xa,ID:1)
[00000427] dmo decoder debug: DMO codec for wmas may work with dll=wmspdmod.dll
[00000427] main decoder debug: using decoder module "dmo"


so choices are to
file bug report on launchpad (to ubuntu vlc packager
request option from a ppa
build your own

use another player
mplayer - all
amarok - all
rhythmbox, similar - wma2, wma3

---

### Post by horde on 2009-08-17
Apologies for asking, but I haven't been able to find the answer yet:

How does one go about compiling VLC with support for these codecs?

---

### Post by andrew.46 on 2009-08-17
Hi horde,

> **horde said:**
> How does one go about compiling VLC with support for these codecs?

If you are considering building vlc you might be interested in an easier option and compile MPlayer which, as mc4man has mentioned, supports all of the files mentioned in part though its external codecs. There is a guide for a 32bit MPlayer here:

HowTo: Install the very latest MPlayer under Jaunty Jackalope
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

which I wrote a while back and seems to work well enough. In my own experience I have found vlc a little more complex to build and as mc4man points out its support of some windows codecs is a little flawed.

All the best,

Andrew

---

### Post by ssri on 2009-09-02
There is a ppa with an svn compiled mplayer.

I tried compiling mplayer the other night and playing wmv's that required wmapro didn't work.  I found this ppa just a few moments ago and it worked for me.  I wish I found this ppa earlier, as it would have saved me a lot of grief.

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Kubuntu Jaunty x86_64
KDE 4.3.1

---

### Post by mc4man on 2009-09-02
> I found this ppa just a few moments ago and it worked for me
That is correct, I believe rvm started appling the wmapro patch in all his mplayer builds in june or thereabouts.

So wma3 decoding is supported (built-in) by his mplayer builds for both i386 and amd_64 ( maybe also the lpia

---

### Post by andrew.46 on 2009-09-02
Hi mc4man,

> **mc4man said:**
> That is correct, I believe rvm started appling the wmapro patch in all his mplayer builds in june or thereabouts.

I may be getting a little impatient but it must be almost time that wmapro was officially unveiled?

Andrew

---

### Post by mc4man on 2009-09-02
> I may be getting a little impatient but it must be almost time that wmapro was officially unveiled?

you would think so . I guess they have their reasons.

Must be a real pita for the patch maintainer, while the patch code hasn't changed in quite some time, the files being patched do, thus requiring  the patch(es) to be adjusted, usually just line number, and or a subsequent line being different. The libavcodec makefile is prone to that.

I've taken to a bit of a reverse shortcut to co ffmpeg, this way just uses 1 command and if part of the patch fails I'll go on in and manually adjust.

```
svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro && cd wmapro && ./checkout.sh

```

---

### Post by andrew.46 on 2009-09-03
Hi mc4man,

> **mc4man said:**
> you would think so . I guess they have their reasons.

Somebody must be listening, looks like wmapro decoder just hit the svn FFmpeg:

```

andrew@skamandros~/source/ffmpeg$ ffmpeg -formats | grep wmapro
FFmpeg version SVN-r19754, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis
 --enable-x11grab --enable-libmp3lame --enable-libx264 
--enable-libschroedinger --enable-libfaac --enable-libfaad
 --enable-libopencore-amrnb --enable-libopencore-amrwb 
--enable-version3 --enable-libgsm --enable-libspeex --enable-zlib 
--enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.35. 0 / 52.35. 0
  libavformat   52.38. 0 / 52.38. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep  3 2009 22:23:58, gcc: 4.3.3
[COLOR="Red"]** D A    wmapro          Windows Media Audio 9 Professional**[/COLOR]

```

Added to [changelog]("http://ffmpeg.org/changelog.html") as well. Very exciting, should be pulled into MPlayer soon enough as well!


Andrew

---

### Post by mc4man on 2009-09-03
> just hit the svn FFmpeg:
As usual you're on top of these things.

It's too bad it probably won't make it into karmic, though overall I'm impressed with the willingness to use recent sources in karmic.

For instance I was looking for a more recent transcode to package for hardy. Whenever possible I prefer a ...orig.tar.gz over a ...tar.gz, Checking the karmic sources I saw they're using transcode_1.1.4.orig.tar.gz which worked quite nicely

For ffmpeg it appears they'll be using the svn from 07/06 which will not as useful as todays or later but  certainly is better than sticking with the 0.5 release (20080303

Will be interesting to see if for the 10.04 release if they use a current ffmpeg or stick with one that karmic uses

---

### Post by andrew.46 on 2009-09-03
Hi mc4man,

> **mc4man said:**
> As usual you're on top of these things.

More a case of me being on leave at the moment and spending far too much time on the computer :-). 

> For instance I was looking for a more recent transcode to package for hardy. Whenever possible I prefer a ...orig.tar.gz over a ...tar.gz, Checking the karmic sources I saw they're using transcode_1.1.4.orig.tar.gz which worked quite nicely

That is a little scary, I was not aware of this release and looks like it only came out on August 23rd!

> For ffmpeg it appears they'll be using the svn from 07/06 which will not as useful as todays or later but  certainly is better than sticking with the 0.5 release (20080303


For my own personal usage the 2 big changes are the move to libopencore-amr and now the wmapro decoder and it looks like karmic may very well miss out on both of those. Although I am not entirely sure of the date the amr switch was made...

Andrew

---

### Post by mc4man on 2009-09-03
> karmic may very well miss out on both of those
They shouldn't have to with the opencore amr, though the ffmpeg source they're using is a bit 'odd'

From the configure --help
> 
 --enable-libamr-nb       enable libamr-nb floating point audio codec [no]
  --enable-libamr-wb       enable libamr-wb floating point audio codec [no]
  --enable-libopencore-amrnb enable AMR-NB de/encoding via libopencore-amrnb [no]
  --enable-libopencore-amrwb enable AMR-WB decoding via libopencore-amrwb [no]


And from the confflags for karmic's diff

> # this part below is intended for the 'ffmpeg' package in ubuntu/multiverse
gpl_confflags += $(call cond_enable,/usr/include/xvid.h,libxvid)
confflags += $(call cond_enable,/usr/include/lame/lame.h,libmp3lame)
gpl_confflags += $(call cond_enable,/usr/include/x264.h,libx264)

confflags += $(call cond_enable,/usr/include/lame/lame.h,libmp3lame)
confflags += $(call cond_enable_nf,/usr/include/amrnb/sp_dec.h,libamr-nb)
confflags += $(call cond_enable_nf,/usr/include/amrwb/dec.h,libamr-wb)


At first apperance it seems the 'stripped' will have no amr and the 'unstripped' will use libamr

(though I'm not 100% sure and it's still early
Maybe I'll build harmic's packages and see, or anyone that has karmic and a 3.gp could tell

---

### Post by andrew.46 on 2009-09-03
Hi mc4man,

We are drifting somewhat from the original topic for which my apologies to the OP :-).

You may be interested to know that Slackware 13.0 features a build of MPlayer for the first time and the build script is quite ingenious as it allows Slackware to distribute mPlayer without the perceived problems of libdvdcss, mp3, faac etc:

[http://slackware.osuosl.org/slackware-13.0/source/xap/MPlayer/MPlayer.SlackBuild](http://slackware.osuosl.org/slackware-13.0/source/xap/MPlayer/MPlayer.SlackBuild)

It is a script that can *easily* be modified by manipulating the USE_PATENTS variable. (This is the same gentleman who looks after the vlc slackbuild I would be lost without!). I will admit that I am not so keen on the karmic solution of using some sort of *shared* libavcodec. My own slackbuild for MPlayer differs somewhat from this one but I will be pillaging some of the ideas from Eric's script :-).

BTW to the OP looks like wmapro decoder is available in an unpatched svn MPlayer now:

```
andrew@skamandros~/source/mplayer$ mplayer -ac help | grep wmapro
ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]
```

Very exciting times!

Andrew

---

### Post by andrew.46 on 2010-02-18
Hi horde,

> **horde said:**
> How does one go about compiling VLC with support for these codecs?

In a flagrant piece of necroposting and self-promotion I can steer you toward a guide which I have written for the development version of vlc which also uses the most recent libavcodec:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

It is written for 32bit Karmic Koala and also enables support for the w32codecs thus creating a copy of vlc that should play *most* files.

All the best,

Andrew

---

### Post by Kangarooo on 2010-03-24
Will it play:
a.) drm wma sound files?
b.) some other codex witch makes error messege for 21 seconds
Codec error: Use Windows Media Player
Aborting Video, Redirecting to Microsoft Codec Download Page

For a.) i know alternative with plays. Mplayer.
But for b.) i havent found yet anything. Installed restricted extras medibuntu all codex dvd codex and some more ive found in some forums. What would work for that?

---

### Post by Kangarooo on 2010-08-17
Ok i found u can play drm wma on linux so also ubuntu with mplayer and that means also smplayer and other same player versions.
so just install mplayer and it will work
> sudo aptitude install mplayer-gui
now also i found some video files also have some protection but thats another topic.
So resume: i have all codecs tryd vlc totem restricted extras and medibuntu and only mplayer plays drm wma music files. Also it would be good if someone checks if on clean installation theese files work on mplayer heres link to one file to ckech on it [http://kangarooo.times.lv/90secondsorless1a.wma](http://kangarooo.times.lv/90secondsorless1a.wma)
and that i can open with mplayer-gui
but i cant open [http://kangarooo.times.lv/03track3.wma](http://kangarooo.times.lv/03track3.wma)
both of them have DRM protection but both act differentin vlc and in mplayer

---

### Post by kistareddyd on 2010-10-04
I was facing a problem to play wmv video . it says that MSS2 and  WMAP codec is not available in your system . so the solution is here i am successfully playing now not cbt nuggets .....

Step-1. Install Mplayer 
Step-2. Install SMplayer

i tried on my Ubuntu 10.04 Lucid version working gre8 guys cheersss............

---

