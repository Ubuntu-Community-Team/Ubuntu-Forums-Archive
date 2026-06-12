---
title: "can you play this video?"
date: 2010-12-14
forum: General Help
---

### Post by sdowney717 on 2010-12-14
[http://www.yachtsilvercloud.com/SSC/movies1.htm](http://www.yachtsilvercloud.com/SSC/movies1.htm)
I was interested in seeing it.
I get the player at the bottom but never plays

---

### Post by Verbeck on 2010-12-14
yes

---

### Post by Spice Weasel on 2010-12-14
"No suitable plugins were found."

---

### Post by sdowney717 on 2010-12-14
how did you do it, what program is working for it to play?

---

### Post by CraigPaleo on 2010-12-14
It plays for me. I have restricted-extras installed.

---

### Post by philinux on 2010-12-14
> **sdowney717 said:**
> [http://www.yachtsilvercloud.com/SSC/movies1.htm](http://www.yachtsilvercloud.com/SSC/movies1.htm)
I was interested in seeing it.
I get the player at the bottom but never plays

Yes and it's using the Totem browser plugin in Firefox. Have you installed ubuntu-restricted-extras and see these.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Moved to General Help forum.

---

### Post by sdowney717 on 2010-12-14
I tried it in Chrome and it plays using the totem plugin, but firefox is using the gnomeplayer plugin

yes, already installed
> Reading state information... Done
ubuntu-restricted-extras is already the newest version.


---

### Post by sdowney717 on 2010-12-14
this is the direct link to the movie.
plays in Chrome not firefox
[http://www.yachtsilvercloud.com/SSC/Movies/SWATH_Comparison.mov](http://www.yachtsilvercloud.com/SSC/Movies/SWATH_Comparison.mov)

---

### Post by Frogs Hair on 2010-12-14
Yes, plays from Opera and Firefox with Gstreamer plugins.

---

### Post by sdowney717 on 2010-12-14
looks like mplayer is broken on the system

scott@scott-desktop:~$ mplayer [http://www.yachtsilvercloud.com/SSC/Movies/SWATH_Comparison.mov](http://www.yachtsilvercloud.com/SSC/Movies/SWATH_Comparison.mov)
mplayer: error while loading shared libraries: libmpcdec.so.3: cannot open shared object file: No such file or directory
scott@scott-desktop:~$ mplayer
mplayer: error while loading shared libraries: libmpcdec.so.3: cannot open shared object file: No such file or directory
scott@scott-desktop:~$

---

### Post by sdowney717 on 2010-12-14
> E: /var/cache/apt/archives/mplayer_2%3a1.0~rc4~try1.dsfg1-1ubuntu1_i386.deb: trying to overwrite '/usr/bin/mplayer', which is also in package mplayer-nogui 2


well it is busted, just uninstalled and reinstall wont go.

---

### Post by sdowney717 on 2010-12-14
got past that error but path is wrong

scott@scott-desktop:~$ mplayer [http://www.yachtsilvercloud.com/SSC/Movies/SWATH_Comparison.mov](http://www.yachtsilvercloud.com/SSC/Movies/SWATH_Comparison.mov)
bash: /usr/local/bin/mplayer: No such file or directory
scott@scott-desktop:~$ 

it is looking for mplayer in usr/local/bin but it is installed in usr/bin

---

### Post by sdowney717 on 2010-12-14
this works, usr/bin/mplayer
the path is pointing to usr/local/bin which wont work

scott@scott-desktop:~$ /usr/bin/mplayer
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

---

### Post by Malta paul on 2010-12-14
I've just checked out your video and its has a .mov extension which means its in 'Quick Time' format. It plays OK with Firefox 3.6.13 with a Quicktime plug-in 7.6.6 installed.

Hope this helps;)

---

### Post by sdowney717 on 2010-12-14
yes, it is installed

mplayer can not start since its path is pointing to usr/local/mplayer
and
my mplayer is installed in usr/mplayer

Guess what, i logged out and in and the path is fixed
so it is working
uninstalling with purge and reinstalling must have affected the path environment and logging back in set the path the way it should be.

---

### Post by andrew.46 on 2010-12-15
Hi sdowney,

Most unusual mix of codecs there:

```

andrew@skamandros~/Desktop$ mplayer SWATH_Comparison.mov 
MPlayer SVN-r32699-4.3.3 (C) 2000-2010 MPlayer Team
Loading extension-related profile 'extension.mov'

Playing SWATH_Comparison.mov.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Audio stream found, -aid 0
[mov] Video stream found, -vid 1
VIDEO:  [SVQ3]  320x240  24bpp  29.963 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
**[COLOR="Red"]Selected video codec: [ffsvq3] vfm: ffmpeg (FFmpeg Sorenson Video v3 (SVQ3))[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 23.9 kbit/1.70% (ratio: 2993->176400)
**[COLOR="Red"]Selected audio codec: [ffqdm2] afm: ffmpeg (FFmpeg QDM2 audio)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 
A:  17.6 V:  18.0 A-V: -0.337 ct:  1.724 540/540  4%  0%  0.3% 1 0 


Exiting... (End of file)

```

But MPlayer rises to the challenge as always :).

Andrew

---

