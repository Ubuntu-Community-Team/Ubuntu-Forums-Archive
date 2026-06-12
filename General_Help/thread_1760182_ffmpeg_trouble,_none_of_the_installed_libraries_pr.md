---
title: "ffmpeg trouble, none of the installed libraries present after typing &quot;ffmpeg&quot;"
date: 2011-05-16
forum: General Help
---

### Post by NaturalBornCamper on 2011-05-16
Hay!

I have a weird problem, or I'm just being stupid. I installed ffmpeg with a load of codecs (mp3lame, vpx, ogg, vorbis, libfaac, libfaad, theora, etc) and they are not in the "ffmpeg -codecs" list or in the "ffmpeg -formats" list.

Upon installation, I entered this:
"./configure --prefix=/usr --libdir=/usr/lib64 --mandir=/usr/share/man --disable-avisynth --enable-avfilter --enable-libfaac --enable-libgsm --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-shared --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab --enable-libvorbis --enable-libvpx --enable-libtheora"
And everything went well after "make && make install", but then, if I just write "ffmpeg", I do not get a single library that was installed, I get this:
" ffmpeg version 0.7_beta2, Copyright (c) 2000-2011 the Libav developers
  built on May 13 2011 12:34:43 with gcc 4.1.2 20080704 (Red Hat 4.1.2-50)
  configuration: 
  libavutil    51.  1. 0 / 51.  1. 0
  libavcodec   53.  3. 0 / 53.  3. 0
  libavformat  53.  0. 3 / 53.  0. 3
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    1.  1. 0 /  1.  1. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
Use -h to get full help or, even better, run 'man ffmpeg'"
Why is "configuration:" empty? Is it because 0.7 version does not give the configuration anymore?


ANYWAY, here's all the info I know and what I tried:
When I try to encode a video like this:
"ffmpeg -i sample.mp4 -vcodec h263 -acodec libfaac -y sample.3gp"
It says:
"Unknown encoder 'libfaac'"

We had 0.6.1 on our server before, installed 0.7 on top of it Friday and upon entering "ffmpeg", it said there were multiple config files. I told myself I would correct this Monday but now there is no configuration, perhaps because of a server reboot.

I checked on the internet how to unsinstall, it said "make clean" and/or "make uninstall". Tried both but ffmpeg is still there afterwards (locate with grep)

In the "./configuration" command, I tried putting incorrect values, like
"--enable-libfaaaaaaac" and it gives me an error message, so it means that it works with the correct synthax "--enable-libfaac"

I have set all the paths after installation:
ln -s /usr/local/lib/libfaac.so.0 /usr/lib/libfaac.so.0
ln -s /usr/local/lib/libfaad.so.2 /usr/lib/libfaad.so.2
ln -s /usr/local/lib/libmp3lame.so.0 /usr/lib/libmp3lame.so.0
ln -s /usr/local/lib/libogg.so.0 /usr/lib/libogg.so.0
ln -s /usr/local/lib/libvorbisenc.so.2 /usr/lib/libvorbisenc.so.2
ln -s /usr/local/lib/libvorbis.so.0 /usr/lib/libvorbis.so.0
ln -s /usr/local/lib/libvorbis.so.0 /usr/lib/libvorbis.so.0
ln -s /usr/local/lib/libtheoradec.so.1 /usr/lib/libtheoradec.so.1
ln -s /usr/local/lib/libtheoraenc.so.1 /usr/lib/libtheoraenc.so.1
ln -s /usr/local/lib/libavcodec.so.52 /usr/lib/libavcodec.so.52
ln -s /usr/local/lib/libavformat.so.52 /usr/lib/libavformat.so.52
ln -s /usr/local/lib/libavutil.so.50 /usr/lib/libavutil.so.50
ln -s /usr/local/bin/ffmpeg2theora /usr/bin/ffmpeg2theora

I have tried that line that was supposed to fix it:
"sudo ldconfig"

Our server is 64bits, but I still managed to compile everything with "-fPIC" when was needed so that is not the problem.

My lib directories has all the libs needed (ls listing):
codecs             libfaac.so.0.0.0     libogg.la              libtheoraenc.so        libvorbisfile.a
libavcodec.a       libfaad.a            libogg.so              libtheoraenc.so.1      libvorbisfile.la
libavcodec.so.52   libfaad.la           libogg.so.0            libtheoraenc.so.1.1.2  libvorbisfile.so
libavdevice.a      libfaad.so           libogg.so.0.7.1        libtheora.la           libvorbisfile.so.3
libavfilter.a      libfaad.so.2         libswscale.a           libtheora.so           libvorbisfile.so.3.3.4
libavformat.a      libfaad.so.2.0.0     libtheora.a            libtheora.so.0         libvorbis.la
libavformat.so.52  libmp3lame.a         libtheoradec.a         libtheora.so.0.3.10    libvorbis.so
libavutil.a        libmp3lame.la        libtheoradec.la        libvorbis.a            libvorbis.so.0
libavutil.so.50    libmp3lame.so        libtheoradec.so        libvorbisenc.a         libvorbis.so.0.4.5
libfaac.a          libmp3lame.so.0      libtheoradec.so.1      libvorbisenc.la        libvpx.a
libfaac.la         libmp3lame.so.0.0.0  libtheoradec.so.1.1.4  libvorbisenc.so        perl5
libfaac.so         libmp4ff.a           libtheoraenc.a         libvorbisenc.so.2      pkgconfig
libfaac.so.0       libogg.a             libtheoraenc.la        libvorbisenc.so.2.0.8


I'm about to throw myself out the window so if anyone has any idea, it would be appreciated.

Thanks!

Marco

---

### Post by NaturalBornCamper on 2011-05-17
Nobody knows?

---

### Post by andrew.46 on 2011-05-18
Are you compiling your copy on Ubuntu? If so this is the guide to follow:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Personally I wold go with the git FFmpeg but I guess you could easily modify the instructions for the release version.

---

### Post by NaturalBornCamper on 2011-05-18
Yeah, I compiled it myself. Tried "apt-remove" as well, but it says:
"Package ffmpeg is not installed, so not removed"

but then, "ffmpeg" still returns
ffmpeg version 0.7_beta2, Copyright (c) 2000-2011 the Libav developers
  built on May 13 2011 12:34:43 with gcc 4.1.2 20080704 (Red Hat 4.1.2-50)
  configuration: 
  libavutil    51.  1. 0 / 51.  1. 0
  libavcodec   53.  3. 0 / 53.  3. 0
  libavformat  53.  0. 3 / 53.  0. 3
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    1.  1. 0 /  1.  1. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
Use -h to get full help or, even better, run 'man ffmpeg'

and "locate ffmpeg" still returns the whole list:
/usr/local/bin/ffmpeg
/usr/local/share/ffmpeg
/usr/local/share/ffmpeg/libx264-baseline.ffpreset
/usr/local/share/ffmpeg/libx264-fast.ffpreset
...

---

### Post by andrew.46 on 2011-05-18
Can I tempt you to look at the Fakeoutdoorsman's guide? This guide has helped people compile FFmpeg under Ubuntu for many years now...

---

### Post by mc4man on 2011-05-18
The interesting thing that you posted is this
> ffmpeg version 0.7_beta2, Copyright (c) 2000-2011 the Libav developers
built on May 13 2011 12:34:43 with gcc 4.1.2 20080704 (Red Hat 4.1.2-50)
What version of Ubuntu are you on?

Anyway to remove a make install you need to cd to your source directory and run sudo make uninstall (if that dir. still exists and hasn't be cleaned.

Otherwise search out and remove _all_ the installed files, if your lucky they are in /usr/local/... and quite see-able
(the other slower way is to rebuild ffmpeg exactly as before, do a sudo make install followed by a sudo make uninstall 
(sudo if whatever your using, doing needs sudo ?

---

### Post by NaturalBornCamper on 2011-05-19
andrew:
Yep, I've already come across FO's guide before, and when I reinstall ffmpeg I will follow the guide. But first I need to delete any trace of ffmpeg as it seems it is still somewhere and the installation is corrupted pretty bad.

mc4man:
I don't exactly have Ubuntu, it's a linux server, but still tried all the ubuntu guides and commands.
Tried "sudo make uninstall"
then "make && make install"
and again "sudo make uninstall", but I still got the same thing:
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)
rmdir "/usr/include"
rmdir: /usr/include: Directory not empty
make: [uninstall-headers] Error 1 (ignored)

Anyway, I was thinking about deleting the folders with all their content myself as you suggested, but it doesn't look clean, as all the symlinks will still be there, no?

Thanks a lot for your time guys

---

