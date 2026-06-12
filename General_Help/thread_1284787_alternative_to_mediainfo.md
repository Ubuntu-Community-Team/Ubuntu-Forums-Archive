---
title: "alternative to mediainfo"
date: 2009-10-07
forum: General Help
---

### Post by kiridude on 2009-10-07
Hi, does anyone know of another program that functions like mediainfo. I am looking for a printout of video or audio quality of a file.

I am having problems with the GPG key of mediainfo and so am looking for an alternative. I keep being told that the key they posted on launchpad is not valid.

Thanks

---

### Post by plucky on 2009-10-07
> **kiridude said:**
> Hi, does anyone know of another program that functions like mediainfo. I am looking for a printout of video or audio quality of a file.

I am having problems with the GPG key of mediainfo and so am looking for an alternative. I keep being told that the key they posted on launchpad is not valid.

Thanks

This command will add the GPG key for the mediainfo PPA assuming you are running Jaunty,copy and paste the command into a terminal window.```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
```

You also need to add this line to your sources.list
```
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main
```

and then ```
sudo apt-get update
```

Good Luck

---

### Post by kiridude on 2009-10-07
Thank you for your reply plucky.

I had already done what you suggested; first by command line, then also through the GUI. Both methods gave me the same error upon update:

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: You may want to run apt-get update to correct these problems

```

Its funny that it suggests I run "apt-get update" as a result of the same command...

---

### Post by plucky on 2009-10-07
Post your sources.list.


Open a terminal and input the command ```
cat /etc/apt/sources.list
``` and post the output to the forum.

---

### Post by mc4man on 2009-10-07
You don't need to add a ppa to get mediainfo ( 3 packages needed). Actually I wouldn't use the ppa, most of the builds there have failed

Also note that for karmic any of the package sets from 8.10 thru 9.04 are really the same packages though [I] used the ones listed in jaunty for karmic

The official builds are here
[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

you need 3 and if downloaded and installed individually the order is this (bottom to top on the page), you don't need the cli package

libzen0
libmediainfo0
gui (mediainfo_gui.0.7.20-1

Or download all 3, put them in a folder, cd to folder in terminal and run
```
sudo dpkg -i *.deb
```

---

### Post by kiridude on 2009-10-07
Plucky, here is my sources.list:

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

deb http://download.skype.com/linux/repos/debian/ stable non-free

deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock

deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main



deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main

```.

---

### Post by kiridude on 2009-10-07
Thanks mc4man, it worked how you suggested.

It's a bit deceiving that they would print, 
"PPA packages
These packages are better included
in your Ubuntu (8.04 to 9.04) distribution,
use them in preference" at the top of the download page when the ppa doesn't work very well.  It is also strange that they would not include all the necessary packages in one download, and further mystifying why they would list the necessary dependencies in a backwards order.

Thanks again.

---

### Post by plucky on 2009-10-07
> deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main



This is the line it is complaining that the GPG key is missing, not the mediainfo line.

To add the key for that line use ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C713DA6
``` should get rid of the warning.

Glad to see you got it working

Good Luck

---

### Post by mc4man on 2009-10-07
A small tip about mediainfo
It's best to always open  a file  in mediainfo's "easy" view, drag and drop works quite well into the mediainfo box.

For extended info then switch to hmtl view, for copying any or all of the extended info switch to text view.
Then return MI to easy view for next file if leaving open

You can have as many open MI windows (instances) a one time as you wish, good  for compares

---

### Post by kiridude on 2009-10-07
Thanks guys

---

### Post by andrew.46 on 2009-10-10
Hi kiridude,

> **kiridude said:**
>  I am looking for a printout of video or audio quality of a file.

Looks like you have solved your problem already but you could consider using FFmpeg to give you some of the details you are after. For example:

```

andrew@skamandros~/samples$ **[COLOR="Red"]ffmpeg -i Rammstein_Du_Hast.mp4 [/COLOR]**
FFmpeg version SVN-r20192, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Oct  9 2009 21:25:41 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter
 --enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libgsm 
--enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 1 /  0. 5. 1
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 49968.00 (49968/1) -> 24.98 (3123/125)
[B][COLOR="Red"]Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Rammstein_Du_Hast.mp4':
  Duration: 00:03:54.10, start: 0.000000, bitrate: 378 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, 2 channels, s16
    Stream #0.1(und): Video: h264, yuv420p, 352x234 [PAR 1:1 DAR 176:117], 24.98 tbr, 24984 tbn, 49968 tbc[/COLOR][/B]
  Metadata
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isomavc1mp42
At least one output file must be specified

```

It may look a little more cumbersome than mediainfo but it is quite effective.

Andrew

---

### Post by kiridude on 2009-10-11
Andrew, that looks interesting - thanks

---

### Post by truant on 2009-10-22
In more recent builds of ffmpeg, such as the one that ships with Karmic,

```
ffmpeg -i FILENAME
```

is the same as

```
ffprobe FILENAME
```

Sadly, this doesn't provide the kind of detailed stream information that mediainfo does - especially in the case of subtitle streams, where I'd like to know what type of subs they are (eg, srt, ssa, whatever).

Guess it's time to get compiling from source, 'cos mediainfo's Karmic PPA is currently dead.

[edit - oh, no, it's fine. The 9.04 debs install OK ]

---

### Post by ron999 on 2009-12-04
> **mc4man said:**
> You don't need to add a ppa to get mediainfo ( 3 packages needed). Actually I wouldn't use the ppa, most of the builds there have failed

Also note that for karmic any of the package sets from 8.10 thru 9.04 are really the same packages though [I] used the ones listed in jaunty for karmic

The official builds are here
[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

you need 3 and if downloaded and installed individually the order is this (bottom to top on the page), you don't need the cli package

libzen0
libmediainfo0
gui (mediainfo_gui.0.7.20-1

Or download all 3, put them in a folder, cd to folder in terminal and run
```
sudo dpkg -i *.deb
```

Thanks for that mc4man.
That worked a treat for me too.
:guitar:

---

### Post by mc4man on 2009-12-04
@ron999

Kinds surprised if you got libzen0 from the official site, there were problems last month getting that .deb

The ppa does seem to be cleaned up now and current, so I'd reommend that now if the 'Official" page doesn't work 
ppa
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

---

### Post by ron999 on 2009-12-05
> **mc4man said:**
> 

The ppa does seem to be cleaned up now and current, so I'd reommend that now ...
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)
OK, I've done that now.
:D

---

### Post by Laysan_A on 2011-06-17
Just wanted to add my experience...

Tried the PPA first and the build failed using apt-get. I removed it and installed with gdebi according to the excellent advice by [mc4man]("http://ubuntuforums.org/member.php?u=320715"). It's great! Maybe not quite as nice as gspot (no troubleshooting), but a lot of info - and it automatically adds itself to the context menu (kde)!

---

