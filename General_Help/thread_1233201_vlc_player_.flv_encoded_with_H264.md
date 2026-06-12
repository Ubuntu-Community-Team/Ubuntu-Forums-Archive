---
title: "vlc player .flv encoded with H264"
date: 2009-08-06
forum: General Help
---

### Post by stoppage on 2009-08-06
Hi, I'm trying to figure out why the vlc player won't play .flv files encoded with H264, when it handles everything else. I've read somewhere that it's dependant on ffmpeg. Is this true? Running Ubuntu Hardy with what I think are latest versions of vlc etc..... 

mplayer - 2:1.0~rc3svn29325-0hardy1 
ffmpeg....3:0.cvs 20070307-5ubuntu7.3+medibuntu1 
vlc....0.9.9a 
mencoder...2:1.0~rc3svn29325-0hardy1
 
The Mplayer plays these files but it's not my player of choice. 

Vlc output for .flv file with h264.... 
„No suitable decoder module: 
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this. 
No suitable decoder module: 
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this“. 
Has anybody found a solution for this....or any help....tearing the hair out! Obliged

---

### Post by stillious on 2009-08-06
Do you have a sample file you could upload somewhere i.e. Rapidshare?

---

### Post by mc4man on 2009-08-06
As mentioned in your other thread vlc uses the shared ffmpeg libs for a lot of decoding. 
As also mentioned I couldn't try the medibuntu ffmpeg libs on my hardy, so booted a live cd, added medibuntu, korn's vlc ect.

The medibuntu ffmpeg and libs can't decode the format your trying to play so consequentially neither will vlc no matter what version or build you install. (or any other app that uses the shared ffmpeg libs.

When a decent libavcodec is installed and vlc is built to use it then playback is possible

> [00000447] main decoder debug: looking for decoder module: 33 candidates
[00000447] avcodec decoder debug: libavcodec initialized (interface 3416064 )
[00000447] avcodec decoder debug: ffmpeg codec (H264 - MPEG-4 AVC (part 10)) started


The ffmpeg decoder used
> Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)



Your options in regards to vlc are quite limited, as in none without building a more current ffmpeg and then vlc off of it.

ffmpeg would need to be built enabling both static and shared libraries, preferably as a debian package set, though probably not 100% necessary in a hardy install

---

### Post by stoppage on 2009-08-06
A sample of the type of  file in question..
[http://www.youtube.com/watch?v=8t4x7VLKm0s&feature=fvhl](http://www.youtube.com/watch?v=8t4x7VLKm0s&feature=fvhl)

mc4man, thank you for all the trouble you've taken over this. I'm not up to building customised ffmpeg, so stuck with mplayer until Medibuntu comes out of the ether..shame really, these files are by no means rare.

---

### Post by stillious on 2009-08-06
Well since it seems VLC is a no-go...

Why not try KMPlayer? I downloaded your sample video as .flv and as .mp4 and both played absolutely fine.

Screenie here: ```
http://imgur.com/yf8eD.png
```

Hope you find a satisfactory solution.

---

### Post by andrew.46 on 2009-08-06
Hi stoppage,

> **stoppage said:**
> A sample of the type of  file in question..
[http://www.youtube.com/watch?v=8t4x7VLKm0s&feature=fvhl](http://www.youtube.com/watch?v=8t4x7VLKm0s&feature=fvhl)

mc4man, thank you for all the trouble you've taken over this. I'm not up to building customised ffmpeg, so stuck with mplayer until Medibuntu comes out of the ether..shame really, these files are by no means rare.

But of course as mc4man has mentioned vlc *can* play the 'high-definition' version of these files it is simply a matter of vlc being correctly built. I downloaded the high-definition version:

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '8t4x7VLKm0s.mp4':
  Duration: 00:02:24.79, start: 0.000000, bitrate: 2117 kb/s
    Stream #0.0(und): **[COLOR="Red"]Audio: aac[/COLOR]**, 44100 Hz, 2 channels, s16
    Stream #0.1(und): **[COLOR="Red"]Video: h264[/COLOR]**, yuv420p, 1280x720
```

and as you mentioned this type of youtube video is by no means rare any more. I attach a screenshot of a custom built vlc 1.0.1 playing this very file.

The best option IMHO will always be building your own although I acknowledge that vlc is not one of the easiest to build. Medibuntu as far as I know has had no interest in vlc which is a pity and I note that with Karmic they have withdrawn their build of MPlayer as well...

Andrew

---

### Post by mc4man on 2009-08-07
Unfortunately building 0.9.9 or 1.x for hardy involves several obstacles that can either be worked around or conceded to.

It appears from a ppa standpoint conceded to is the more likely path.

Without more current shared ffmpeg libs, a hardy install, from a multimedia perspective, is somewhat outdated already.

It will be interesting to see how korn's vlc 1.0.1 turns out, the first build failed though the the immediate error is easily corrected, 
(( the modplug module cannot be built from the hardy lib, so the fix is either use the jaunty/karmic version or remove the mod plugin.

If he decides to continue, users of that ppa may end up with the latest vlc with some of the new features, but, **depending on one's usage**, a less function-able vlc than the 0.9.9.a it's replacing.

(( it's still using the old libavcodec's so nothing improved there.

Users of korn's vlc ppa for hardy, if/when the build succeeds, may want to consider and ask about the gain versus loss, and not update blindly

---

### Post by andrew.46 on 2009-08-07
Hi mc4man,

> **mc4man said:**
> Unfortunately building 0.9.9 or 1.x for hardy involves several obstacles that can either be worked around or conceded to.

Sounds fascinating and I accept the challenge :-). I have just installed 8.0.4-3 onto a VM and I shall tinker with it for a day or three and see if I can get a decent copy of vlc 1.0.1 running...

Andrew

---

### Post by andrew.46 on 2009-08-07
Hi,

Epic fail building vlc 1.0.1 under Hardy :-). So many libraries are considered out of date by the new vlc; that was a compile-fest I do not want to repeat soon! I have great respect for anybody who succeeds with this one...

Andrew

---

### Post by luigi_mb on 2009-08-07
> **andrew.46 said:**
> Hi,

Epic fail building vlc 1.0.1 under Hardy :-). So many libraries are considered out of date by the new vlc; that was a compile-fest I do not want to repeat soon! I have great respect for anybody who succeeds with this one...

Andrew

Did you look at the list of dependencies at

[http://www.videolan.org/developers/vlc.html](http://www.videolan.org/developers/vlc.html)

I was able to build v1.0.1 on Ubuntu v9.04, using default configuration. It does play the youtube file mentioned earlier.

/luigi

---

### Post by mc4man on 2009-08-08
It's actually not quite as involved as it appears at first, though to build for an absolutely stock hardy would result in a fairly neutered vlc.

the main key is ffmpeg and by extension libx264, after that many of the modules on a personal basis probably wouldn't be needed and can be disabled.

On the other hand most of those modules can be enabled by using updated packages which are 'dead-ended' so to speak or are different names so they can co-exist with current hardy one's.

 my main hardy has been modded to such an extent that to comment in regards to building 1.0.1 on that is worthless

I do have a stock install that can build 1.0.x with very little changed, the main upgrades were ffmpeg built as static and shared, a libx264 static and shared.
After that i updated these though they could also be disabled in the build

> doug@doug-desktop:~/Desktop/vlc1.x-deps$ ls *.deb
libdvbpsi5_0.1.6-1_i386.deb         libtag1-dev_1.5-3_i386.deb
libdvbpsi5-dev_0.1.6-1_i386.deb     libv4l-0_0.5.8-1_i386.deb
libmtp8_0.3.0-1ubuntu1_i386.deb     libv4l-dev_0.5.8-1_i386.deb
libmtp-dev_0.3.0-1ubuntu1_i386.deb  libxcb-keysyms0_0.2+git36-1_i386.deb
libtag1c2a_1.5-3_i386.deb           libxcb-keysyms0-dev_0.2+git36-1_i386.deb


The configure from the last non package build of vlc on the almost stock hardy
> main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr' '--disable-zvbi' '--enable-flac' '--enable-libass' '--enable-caca' '--enable-faad' '--disable-kate' '--enable-twolame' '--enable-theora' '--with-x264-tree=/usr/include' '--enable-cddax' '--disable-fluidsynth' '--with-live555-tree=/usr/lib/live' '--enable-loader' '--with-tuning=native' '--disable-nls' '--disable-mozilla' '--disable-mod' '--enable-real' '--enable-realrtsp' '--disable-pulse'

The configure of the package version done on this machine when 1.0.1 released. (note the config is bloated, most of the enables are already a default
> VLC media player 1.0.1 Goldeneye
[COLOR="Red"]LibVLC has detected an unusable buggy GNU/libc version.[/COLOR]
Please update to version 2.8 or newer.
[0x8051140] main libvlc debug: VLC media player - version 1.0.0 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x8051140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--with-tuning=native' '--prefix=/usr' '--config-cache' '--enable-loader' '--disable-schroedinger' '--enable-fast-install' '--disable-pulse' '--with-binary-version=1~ppa4' '--disable-update-check' '--disable-fb' '--enable-cddax' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack'  '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--disable-mozilla' '--disable-nls' '--disable-fluidsynth' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--with-live555-tree=/usr/lib/live' '--enable-svgalib' 'build_alias=i486-linux-gnu'
The red is the result of libc6 on hardy, the one enduring limitation that even on my modded install is not worth changing ( in this build i did add a few more modules, - mod, cddax, mpc and used a package version of libx264-67 and matching -dev

for ffmpeg i used SVN-r19087 with the wmapro patch and libx264-67 though a bit lower would also work

(( what i find much more interesting is the extent that hardy can be brought forward, with the exception of libc6 as or** more capable than jaunty**, (the glib version hasn't been much of a restriction as of yet.

Plus the use of a local repo has proved to be very useful and educational.

For myself It's useful on my desktop, which was at one time a high end p4. For hardware like that hardy is ideal, jaunty much less so.

Even on my core2duo laptop i'm using a modded hardy over jaunty though karmic looks like it may be very good, particularly for more current hardware.

---

### Post by mc4man on 2009-08-11
Forgot all about this post which gives the min. working config. for building vlc 1.0.x on hardy with only 1 updated lib - libx264 (a must), would work thru 1.0.2

[http://ubuntuforums.org/showthread.php?p=7597525#post7597525](http://ubuntuforums.org/showthread.php?p=7597525#post7597525)

I'd think the korn vlc ppa's hardy 1.0.x would be about the same config when built, though maybe he'll add some updated libraries to the ppa or find another way.
(( though the most useful one - ffmpeg, will not likely be one

---

