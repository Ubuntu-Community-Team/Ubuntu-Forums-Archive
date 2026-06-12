---
title: "** Ubuntu Restricted Extras + Synaptic **"
date: 2010-01-07
forum: General Help
---

### Post by Evie~ on 2010-01-07
Guys, I'm really flakin' out here.

 I have been trying to find out how to do this for DAYS, to no avail. Searched previous topics on this subject + installing Flash etc, but none of them seem to be working for me...

 I tried Synaptic but it confused me a helluva lot... It said it had installed all the packages, but I restarted Firefox to check what plugins I had & tried to play my MP3's... only to find out there was nothing there & I still couldn't play my music.

 I've tried the .tar.gz technique, where you create the plugins folder in a hidden .mozilla one inside your home folder, & extract the file into the plugins folder and it's supposed to magically work - it didn't :c

 I've figured out the software source thing and all that jazz, luckily (I hope :x).

 Could you please give me a step-by-step guide on how to install the package and do what I need to do? I'm still a bit of a novice with this, but I'm happy to learn new things and persevere.

 Thanks so much for your help I've received for other issues so far, I haven't lost faith in Ubuntu yet because of all your friendly & detailed advice ;)

---

### Post by snowpine on 2010-01-07
Applications->Accessories->Terminal

copy & paste these exact commands:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

it's that simple... post any errors you get here.

---

### Post by Evie~ on 2010-01-07
Ahhh, stuck at 2% on first line, connecting :(
Is it something to do with where I'm downloading it from?
I'm from New Zealand so my selection isn't huge; 3.

---

### Post by snowpine on 2010-01-07
I think if you go into System->Admininstration->Software Sources (not in front of an Ubuntu machine at the moment), you can try switching to a different mirror.

---

### Post by Evie~ on 2010-01-07
Yeah, only 1 of them will work when I'm downloading something.
Would it make any difference if I chose one from a different country?

---

### Post by Enigmapond on 2010-01-07
Right System->Administration->Software Sources->Download From and check other, then have it poll for the fastest source available from your area.

---

### Post by Evie~ on 2010-01-07
I tried that, too... D:
EDIT: I decided to go through mirrors in NZ again, and after it selected one and I updated whatever it asked me to, I got "**Could not download all repository indexes**", and it hasn't done that before.
Hmmm.

P.S., I just attempted to install Flash via .deb, worked fine until it almost finished and spat out "**Error: Dependency is not satisfiable: libnspr4-dev**"

---

### Post by Evie~ on 2010-01-07
Bump? :(

---

### Post by snowpine on 2010-01-07
Not really enough details to guess what the problem is.

Try the following commands, and copy & paste the terminal output here.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Evie~ on 2010-01-07
> **snowpine said:**
> Not really enough details to guess what the problem is.

Try the following commands, and copy & paste the terminal output here.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

First one results as this below, just sitting there and not doing anything.
```
2% [Connecting to nz2.archive.ubuntu.com (1.0.0.0)] [Connecting to archive.canonical.com (1.0.0.0)]
```Second one separately results as this.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-installer freepats gstreamer0.10-ffmpeg
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse liba52-0.7.4 libass3 libavcodec52
  libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0
  libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1
  libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libjack0 libkate1
  libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0
  libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51
  libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0
  libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4
  ttf-liberation ttf-mscorefonts-installer unrar
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs libdvdcss2 debhelper fakeroot
  build-essential libfftw3-dev jackd sidplay-base xsidplay
Recommended packages:
  w32codecs
The following NEW packages will be installed:
  cabextract flashplugin-installer freepats gstreamer0.10-ffmpeg
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse liba52-0.7.4 libass3 libavcodec52
  libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0
  libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1
  libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libjack0 libkate1
  libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0
  libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51
  libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0
  libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4
  ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unrar
0 upgraded, 58 newly installed, 0 to remove and 168 not upgraded.
Need to get 43.7MB of archives.
After this operation, 75.1MB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  cabextract flashplugin-installer freepats libavutil49 libgsm1
  libschroedinger-1.0-0 libavcodec52 libavformat52 libpostproc51 libswscale0
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll libenca0 libass3 libcdaudio1
  libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvdread4 libdvdnav4 libfaad0
  libiptcdata0 libxml++2.6-2 libffado1 libfreebob0 libjack0 libkate1 libmimic0
  libmms0 libmodplug0c2 libmpcdec3 libfftw3-3 libofa0 libopenspc0
  libsoundtouch1c2 libwildmidi0 gstreamer0.10-plugins-bad libfaac0
  libquicktime1 libmjpegtools-1.9 libxvidcore4
  gstreamer0.10-plugins-bad-multiverse liba52-0.7.4 libid3tag0 libmad0
  libmpeg2-4 libsidplay1 libtwolame0 gstreamer0.10-plugins-ugly libmp3lame0
  libx264-67 gstreamer0.10-plugins-ugly-multiverse libmp4v2-0 ttf-liberation
  ttf-mscorefonts-installer ubuntu-restricted-extras unrar
Install these packages without verification [y/N]? y
0% [Connecting to nz2.archive.ubuntu.com (1.0.0.0)] 
```Yeah, then it just sits there.

EDIT: Uh, it just said it failed to connect and then told me this;
```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by snowpine on 2010-01-07
Definitely looks to me like the NZ mirror is down... you can try a different mirror or wait a little while (these things are usually temporary).

Other than not being able to connect, everything looks ok. :)

---

### Post by Evie~ on 2010-01-07
Okay, much appreciated snowpine, good to know it's nothing major. Sorry it turned out to be something so simple, haha :P

---

