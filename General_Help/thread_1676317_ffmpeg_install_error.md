---
title: "ffmpeg install error"
date: 2011-01-27
forum: General Help
---

### Post by vogskis on 2011-01-27
hello all.  i am having issues trying to install ffmpeg and x264 on my  VE server.  here is the guide i am following...  [http://ubuntuforums.org/showpost.php?p=9114176&postcount=967](http://ubuntuforums.org/showpost.php?p=9114176&postcount=967).

and below is a printscreen of the error message i am receiving when i run:

[FONT=monospace]# [/FONT]checkinstall  --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`+`git rev-list HEAD  -n 1 | head -c 7`" --backup=no --default --deldoc=yes


[IMG]http://205.186.154.214/ex264.jpg[/IMG]

i believe it has something to do with the permissions of the 'installwatch' 'installscript.sh' and '/bin/sh' directories.  but i'm unsure and waiting for assistance on what to do next...

---

### Post by djeikyb on 2011-01-27
It's hard to tell what exactly is going on here, I feel like there is important text missing. But initially, it looks like one (or both) of two things.

(1) The script is trying to run `make install` as a normal user, when it should be run as root. Try again using the sudo command.

(2) The script is using the wrong shell. Maybe it's expecting bash, and Ubuntu is retardedly forcing it to use dash. Not sure how to fix it if this is the case.

---

### Post by FakeOutdoorsman on 2011-01-27
What's a VE server? I would guess you have non-standard permissions in */var/tmp*. See [bad interpreter: Permission denied when installing x264](http://ubuntuforums.org/showthread.php?p=9614476#post9614476) and continue to the next page for a possible solution.

---

### Post by vogskis on 2011-01-28
thanks for the feedback, although still no success.

the VE server is hosted by mediatemple.  [here's a tutorial for 'securing' the server, which may have limited my permissions]("http://wiki.mediatemple.net/w/VE:Secure_your_server").  and i'm using Ubuntu Karmic 9.10.

i ran the command 'mount | grep noexec' and it was very different from the other ron999's.

here's the output...
```

root@ve:/# mount | grep noexec
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

i tried following the '[GETTING AROUND TMPFS NO EXEC]("http://serialized.net/2010/03/getting-around-tmpfs-noexec-problems")' but this is what happened...

```
Installing with make...Installing with install...

========================= Installation results ===========================
install -d /usr/local/bin
install -d /usr/local/include
install -d /usr/local/lib
install -d /usr/local/lib/pkgconfig
install -m 644 x264.h /usr/local/include
install -m 644 x264_config.h /usr/local/include
install -m 644 libx264.a /usr/local/lib
install -m 644 x264.pc /usr/local/lib/pkgconfig
install x264 /usr/local/bin
ranlib /usr/local/lib/libx264.a

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./COPYING
./doc/
./doc/ratecontrol.txt
./doc/regression_test.txt
./doc/standards.txt
./doc/threads.txt
./doc/vui.txt
grep: /var/tmp/tmp.7GH6EJk9AL/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: y

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK

root@ve:~/x264#
```


not sure what went wrong here....

---

### Post by FakeOutdoorsman on 2011-01-28
> **vogskis said:**
> thanks for the feedback, although still no success.

the VE server is hosted by mediatemple.  [here's a tutorial for 'securing' the server, which may have limited my permissions]("http://wiki.mediatemple.net/w/VE:Secure_your_server").  and i'm using Ubuntu Karmic 9.10.

Doesn't look like anything in that tutorial would cause this issue.

> **vogskis said:**
> i ran the command 'mount | grep noexec' and it was very different from the other ron999's.

here's the output...
```

root@ve:/# mount | grep noexec
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

There goes my guess. I don't know what's wrong. I reveal my ignorance.

> **vogskis said:**
> 
```
*** Failed to build the package

Do you want to see the log file?  [y]: y
```
Did the log file show anything of interest?

---

### Post by sserdyuk on 2011-03-11
I second this error. I am compiling a fresh ffmpeg setup on an Ubuntu Hardy server using these instructions [http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)

I've gotten to the last checkinstall and it fails with a similar message

```

root@www:~/sources/ffmpeg# sudo checkinstall --pkgname=ffmpeg --pkgversion="4:$(./version.sh)" --backup=no --deldoc=yes --default --fstrans=no

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@www.drm.com ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ ffmpeg ]
3 -  Version: [ 4:UNKNOWN ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ffmpeg ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
INSTALL	libavdevice/libavdevice.a
INSTALL	libavfilter/libavfilter.a
INSTALL	libavformat/libavformat.a
INSTALL	libavcodec/libavcodec.a
INSTALL	libpostproc/libpostproc.a
INSTALL	libswscale/libswscale.a
INSTALL	libavutil/libavutil.a
INSTALL	libavdevice/avdevice.h
INSTALL	libavdevice/libavdevice.pc
INSTALL	libavfilter/avfilter.h
INSTALL	libavfilter/avfiltergraph.h
INSTALL	libavfilter/libavfilter.pc
INSTALL	libavformat/avformat.h
INSTALL	libavformat/avio.h
INSTALL	libavformat/version.h
INSTALL	libavformat/libavformat.pc
INSTALL	libavcodec/avcodec.h
INSTALL	libavcodec/avfft.h
INSTALL	libavcodec/dxva2.h
INSTALL	libavcodec/opt.h
INSTALL	libavcodec/vaapi.h
INSTALL	libavcodec/vdpau.h
INSTALL	libavcodec/xvmc.h
INSTALL	libavcodec/libavcodec.pc
INSTALL	libpostproc/postprocess.h
INSTALL	libpostproc/libpostproc.pc
INSTALL	libswscale/swscale.h
INSTALL	libswscale/libswscale.pc
INSTALL	libavutil/adler32.h
INSTALL	libavutil/attributes.h
INSTALL	libavutil/audioconvert.h
INSTALL	libavutil/avassert.h
INSTALL	libavutil/avstring.h
INSTALL	libavutil/avutil.h
INSTALL	libavutil/base64.h
INSTALL	libavutil/bswap.h
INSTALL	libavutil/common.h
INSTALL	libavutil/cpu.h
INSTALL	libavutil/crc.h
INSTALL	libavutil/error.h
INSTALL	libavutil/eval.h
INSTALL	libavutil/fifo.h
INSTALL	libavutil/file.h
INSTALL	libavutil/imgutils.h
INSTALL	libavutil/intfloat_readwrite.h
INSTALL	libavutil/intreadwrite.h
INSTALL	libavutil/lfg.h
INSTALL	libavutil/log.h
INSTALL	libavutil/lzo.h
INSTALL	libavutil/mathematics.h
INSTALL	libavutil/md5.h
INSTALL	libavutil/mem.h
INSTALL	libavutil/opt.h
INSTALL	libavutil/parseutils.h
INSTALL	libavutil/pixdesc.h
INSTALL	libavutil/pixfmt.h
INSTALL	libavutil/random_seed.h
INSTALL	libavutil/rational.h
INSTALL	libavutil/samplefmt.h
INSTALL	libavutil/sha1.h
INSTALL	libavutil/avconfig.h
INSTALL	libavutil/libavutil.pc
INSTALL	ffmpeg
INSTALL	ffprobe
INSTALL	ffserver
INSTALL	ffpresets/libx264-baseline.ffpreset
INSTALL	ffpresets/libx264-faster.ffpreset
INSTALL	ffpresets/libx264-faster_firstpass.ffpreset
INSTALL	ffpresets/libx264-fast.ffpreset
INSTALL	ffpresets/libx264-fast_firstpass.ffpreset
INSTALL	ffpresets/libx264-ipod320.ffpreset
INSTALL	ffpresets/libx264-ipod640.ffpreset
INSTALL	ffpresets/libx264-lossless_fast.ffpreset
INSTALL	ffpresets/libx264-lossless_max.ffpreset
INSTALL	ffpresets/libx264-lossless_medium.ffpreset
INSTALL	ffpresets/libx264-lossless_slower.ffpreset
INSTALL	ffpresets/libx264-lossless_slow.ffpreset
INSTALL	ffpresets/libx264-lossless_ultrafast.ffpreset
INSTALL	ffpresets/libx264-main.ffpreset
INSTALL	ffpresets/libx264-medium.ffpreset
INSTALL	ffpresets/libx264-medium_firstpass.ffpreset
INSTALL	ffpresets/libx264-placebo.ffpreset
INSTALL	ffpresets/libx264-placebo_firstpass.ffpreset
INSTALL	ffpresets/libx264-slower.ffpreset
INSTALL	ffpresets/libx264-slower_firstpass.ffpreset
INSTALL	ffpresets/libx264-slow.ffpreset
INSTALL	ffpresets/libx264-slow_firstpass.ffpreset
INSTALL	ffpresets/libx264-superfast.ffpreset
INSTALL	ffpresets/libx264-superfast_firstpass.ffpreset
INSTALL	ffpresets/libx264-ultrafast.ffpreset
INSTALL	ffpresets/libx264-ultrafast_firstpass.ffpreset
INSTALL	ffpresets/libx264-veryfast.ffpreset
INSTALL	ffpresets/libx264-veryfast_firstpass.ffpreset
INSTALL	ffpresets/libx264-veryslow.ffpreset
INSTALL	ffpresets/libx264-veryslow_firstpass.ffpreset
INSTALL	doc/ffmpeg.1
INSTALL	doc/ffprobe.1
INSTALL	doc/ffserver.1

======================== Installation successful ==========================

Copying documentation directory...
./
./COPYING.LGPLv2.1
./INSTALL
./COPYING.LGPLv3
./README
./doc/
./doc/ffserver.html
./doc/soc.txt
./doc/rate_distortion.txt
./doc/developer.texi
./doc/demuxers.texi
./doc/general.html
./doc/general.html.d
./doc/indevs.texi
./doc/fftools-common-opts.texi
./doc/build_system.txt
./doc/viterbi.txt
./doc/bitstream_filters.texi
./doc/ffprobe.html.d
./doc/ffserver.1
./doc/developer.html
./doc/snow.txt
./doc/ffmpeg.texi
./doc/ffserver.pod
./doc/libavfilter.texi
./doc/TODO
./doc/libavfilter.html
./doc/faq.html
./doc/git-howto.txt
./doc/developer.html.d
./doc/ffprobe.pod
./doc/ffmpeg.pod.d
./doc/ffmpeg.pod
./doc/muxers.texi
./doc/ffprobe.html
./doc/ffmpeg.1
./doc/ffserver.pod.d
./doc/APIchanges
./doc/optimization.txt
./doc/faq.html.d
./doc/ffprobe.texi
./doc/ffprobe.1
./doc/ffmpeg.html
./doc/tablegen.txt
./doc/issue_tracker.txt
./doc/ffserver.texi
./doc/general.texi
./doc/ffprobe.pod.d
./doc/t2h.init
./doc/filters.texi
./doc/multithreading.txt
./doc/eval.texi
./doc/texi2pod.pl
./doc/encoders.texi
./doc/ffserver.html.d
./doc/ffserver.conf
./doc/ffmpeg.html.d
./doc/swscale.txt
./doc/faq.texi
./doc/ffplay.texi
./doc/metadata.texi
./doc/libavfilter.html.d
./doc/protocols.texi
./doc/outdevs.texi
./doc/avutil.txt
./COPYING.GPLv3
./LICENSE
./Changelog
./COPYING.GPLv2
./CREDITS
grep: /var/tmp/iBdEicOaNooEqLCGQhheq/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: y

Erasing temporary files...OK

Deleting temp dir...OK

```

---

### Post by mc4man on 2011-03-11
try adding this to your checkinstall command
 --fstrans=no 
Ex.
```
sudo checkinstall --pkgname=ffmpeg --pkgversion="4:$(./version.sh)" --backup=no \
--deldoc=yes --default  --fstrans=no 
```

---

### Post by sserdyuk on 2011-03-11
Unfortunately, made no difference. What information should I share here to aid with troubleshooting?

> **mc4man said:**
> try adding this to your checkinstall command
 --fstrans=no 
Ex.


---

### Post by sserdyuk on 2011-03-12
This is the log file that pops up:
```

dpkg-deb - error: (upstream) version (`UNKNOWN') doesn't contain any digits
dpkg-deb: 1 errors in control file
/var/tmp/lLWEdEZXWShHiDpBXMYgI/dpkgbuild.log (END) 

```

So I looked at the command and noticed it runs './version.sh' to make the version number. I edited this script to return 'UNKNOWN123' instead of 'UNKNOWN' and that fixed everything. The 'No such file or directory' message is still shown but checkinstall now finishes and package is installed.

---

### Post by sserdyuk on 2011-03-12
Actually, it would be nice to update these instructions to simply change the checkinstall command to something like:

```

sudo checkinstall --pkgname=ffmpeg --pkgversion="4:$0(./version.sh)" --backup=no --deldoc=yes --default

```

so it doesn't fail even if ./version returns an alpha string.

---

### Post by stphnlee on 2011-05-18
I wanted to use ffmpeg for my Drupal site hosted on MediaTemple but also ran into the same problem. I never got it to work and wound up using a different method entirely. I'd be interested to know if anyone comes up with a solution though...

---

