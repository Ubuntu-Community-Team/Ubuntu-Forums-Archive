---
title: "ffmpeg broke, all output files empty now!"
date: 2009-09-05
forum: General Help
---

### Post by Cephi on 2009-09-05
Help, my ffmpeg broke!  It was working fine before.  I installed some libs to play encrypted dvds on my computer, could that be what broke it?  I think I followed these directions ([http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html](http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html) ), except libdvd4 instead of libdvd3.

Anyway, when I run an ffmpeg command like the following, I get the following result plus an empty output file.  

> ffmpeg -i n4.vob testfile
FFmpeg version git-91be88c, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-shared --enable-pthreads --enable-libx264 --enable-libfaac --enable-libtheora
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.20. 0
  libavformat   52.36. 0 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 24 2009 21:22:03, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from 'n4.vob':
  Duration: 00:05:22.25, start: 0.500000, bitrate: 3909 kb/s
    Stream #0.0[0x1e0], 1/90000: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 1001/60000, 104857 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80], 1/90000: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_channel_layout_num_channels


(Weirdly, when I try this with the -ss, -t, -vcodec and -acodec options I need to use for what I'm doing, not only do I get an empty output file, but my terminal gets messed up!  My input doesn't show on the screen, but the terminal still behaves as though I'm typing normally -- if I type "ls [Enter}", I don't see "ls", but I do see the result of the command.  I have to use "reset" to fix the term.)

Ideas?  I really need my ffmpeg back!

---

### Post by Cephi on 2009-09-05
Here's someone who had the same problem and found a solution... but I don't understand what they say, or what I'm supposed to do :(

Someone decode plz?

[http://www.linuxquestions.org/questions/linux-software-2/ffmpeg-undefined-symbol-error-for-avcodecchannellayoutnumchannels-736341/](http://www.linuxquestions.org/questions/linux-software-2/ffmpeg-undefined-symbol-error-for-avcodecchannellayoutnumchannels-736341/)

---

### Post by mc4man on 2009-09-05
Not exactly sure what you did or what release of ubuntu you're on.

It appears you built a recent ffmpeg as shared (to /usr/local) and either didn't run
```
sudo ldconfig
```
or did run the above but it's not linking properly because of existing ffmpeg shared libs in /usr

So try above command and see.

(( While I'm not sure if it's 100% necessary I prefer to build a shared ffmpeg as a debian package set, then there are no linking issues

---

### Post by Cephi on 2009-09-05
Tried that, it had no apparent effect.  I'm afraid your last statement goes over my head.  I'm running Jaunty, btw.

---

### Post by Cephi on 2009-09-05
Also just tried purging and reinstalling ffmpeg per instructions here: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095).  No change.

If I can't get around this I'll have to reinstall Jaunty and wow I sure don't want to do that.  Any thoughts appreciated.

---

### Post by WindPower on 2009-09-06
If you want to take the hackish route, you can take the ffmpeg binary that I package in [DamnVid](http://damnvid.googlecode.com/) (Source -> Browse -> trunk -> bin -> ffmpeg (or ffmpeg64 for 64-bit)) and replace your system's one with this. It has all libraries you could ask for ;)

---

### Post by mc4man on 2009-09-06
> Also just tried purging and reinstalling ffmpeg per instructions here: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095). No change.

If I can't get around this I'll have to reinstall Jaunty and wow I sure don't want to do that. Any thoughts appreciated. 

There should be no need to re install jaunty to fix. Your orig. post impiles  that the ffmpeg you built (git-91be88c) was working until you ran the .sh that install libdvdcss2.

When you install a package, at the end of the install a ldconfig is run. 
At this point you also indicate ffmpeg stopped working

The most likely reason is because you built ffmpeg as shared ( most likely to /usr/local) and probably also have ffmpeg shared libraries previously installed (in /usr) 
Maybe you don't, though the odds are you do. 

While I think you could possibly get away with that, it could easily cause issues like your seeing. ( as could having multiple ffmpeg's installed

Rather than re-install jaunty just remove ffmpeg and all it's libraries, shared and static.
Then re- install the the checkinstall .deb you made from F.O.'s how to

You may lose some players and or plugins but those can be reinstalled


So I'd search ffmpeg in synaptic and remove it and any ffmpeg lib packages installed
libavcodecXX, libavformatXX, libpostprocXX, libswscale, ect.

Then look in the filesystem for anything else not removed, places to look are (look for both ffmpeg and libavcodec, libavformat, ect.
/usr/lib
/usr/lib//pkgconfig
/usr/include
/usr/bin
and the same in /usr/local  (more likely place  you may find anything

If the checkinstall ffmpeg you built wasn't built as shared you won't have any issues when or if package versions of libavcodecXX, ect. are re-installed.
If you built the .deb with --enable-shared you may be alright, you may not

---

### Post by Cephi on 2009-09-06
> **mc4man said:**
> Rather than re-install jaunty just remove ffmpeg and all it's libraries, shared and static.
Then re- install the the checkinstall .deb you made from F.O.'s how to.

Ahh lifesaver, thanks this worked.  I had already tried removing and reinstalling ffmpeg but I hadn't removed all the libraries that first time, which apparently made all the difference.

Also WindPower thanks for the suggestion.

---

