---
title: "need a good converter,  winff gives error unknown encoder"
date: 2009-10-12
forum: General Help
---

### Post by sdowney717 on 2009-10-12
according to synaptic coder is installed, look at picture

trying to make an mpeg-4 video?? from a mpg file

> Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from '/home/scott2/vlc-record-2009-10-12-23h40m44s-video0-.mpg':
  Duration: 00:00:08.39, start: 18617.699600, bitrate: 4716 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 8000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 224 kb/s
Unknown encoder 'libx264'
Press Enter to Continue


---

### Post by P4man on 2009-10-13
try handbrake
[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by paul.gevers on 2009-10-13
> **sdowney717 said:**
> according to synaptic coder is installed, look at picture

ffmpeg (winff is the gui for that) comes with it's own libraries. You need libavcodec-unstripped-51 or libavcodec-unstripped-52 or libavcodec-extra-52 (depending on which version of Ubuntu you are running).

---

### Post by sdowney717 on 2009-10-13
thanks, i installed those, now i am getting this
Unknown encoder 'libfaac'

libfaac is installed according to synaptic

---

### Post by rampageoberon on 2009-10-13
> **sdowney717 said:**
> according to synaptic coder is installed, look at picture

trying to make an mpeg-4 video?? from a mpg file

Perhaps Avidemux?

---

### Post by paul.gevers on 2009-10-14
> **sdowney717 said:**
> thanks, i installed those, now i am getting this
Unknown encoder 'libfaac'

libfaac is installed according to synaptic

Are you running Ubuntu Karmic? libfaac has not been build into ffmpeg in Ubuntu because it is deemed non-free.

It is a bug that the libfaac containing presets are still present in winff. I don't know what would be a good replacement.

---

### Post by nothingspecial on 2009-10-14
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1117283")

---

### Post by sdowney717 on 2009-10-14
yes, karmic beta.
i tried installing restricted extra etc... but they all said they were the latest versions

---

### Post by mc4man on 2009-10-14
> i tried installing restricted extra etc..

The ubuntu-restricted-extras isn't going to be of much value here. 
( it also probably only installs the slightly stripped ffmpeg libs instead of the 'extra' versions. Wouldn't actually know, never have installed it, just looking at the recommends, libavcodec52, libavformat52, ect.

You have several choices to enable aac encoding in karmic thru ffmpeg. 

The best I think is build your own, enabling shared libs. Again there are several methods, I prefer to apply a suitable debian .diff to the ffmpeg revision I want to use and build/install as a package set to /usr ( you could also probably just build ffmpeg as shared to /usr/local and link

In this case the set is 15 packages and serves as a replacement to the repo versions and maintains deps with repo packages that depend on the ffmpeg libs.

If you were to build you'd need to decide on method and also whether to use a current svn or one prior to about 09/24. ( don't have the specific -r handy.
Any of the more current svn's will require a newer libx264 (min 76), while prior will be ok with the repo or slightly newer versions ( 67, 68, 75


You could also probably just do an apt-get build-dep and apt-get source ffmpeg and build the current karmic source with fakeroot

There are confflags in the karmic source that will enable the 'non-free' codecs as long as the proper -dev's are installed prior to build ( libfaac-dev, libamrnb-dev, ect.

I don't particularly like the ubuntu source or it's diff but that's just my opinion. ( if one was to do that note that while the packages produced will install as a 're-install', some of them will be immediately be seen as a lower version than the repo's. You would want to append a -1 to the version #'s in the control file to prevent that 


You could also look for a ppa that offers ffmpeg and it's libs with aac encoding enabled.

I'd be wary of any that offer a current ffmpeg source, they may or may not break break decoding in some repo apps like vlc and totem.
Any that shows builds from early sept or before would probably be good. The other give away would be if the ppa had a libx264-76 as a dep

EDit: tried 3 ppa's that had a newer ffmpeg and libs for karmic, all had issues

screen shows my preferred method, have both any earlier (-r19777) set and this from 10/01 ( -r20130 )

Note that winff worked fine with the -r19777 as a test, haven't tried the later, don't actually use winff

---

### Post by benjamimgois on 2009-10-17
I'm with the same problem here, it used work just fine on Jaunty 32bit. The problem began after i update to Karmic 64bit.

---

### Post by kvarley on 2009-10-17
[Handbrake]("http://handbrake.fr"), [kdenlive]("http://www.kdenlive.org/") or [avidemux.]("http://fixounet.free.fr/avidemux/")

---

