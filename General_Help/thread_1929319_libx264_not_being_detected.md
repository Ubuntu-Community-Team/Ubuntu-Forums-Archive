---
title: "libx264 not being detected"
date: 2012-02-21
forum: General Help
---

### Post by rzippert on 2012-02-21
Hello encoders =)

Right now I'm trying to set my encoding software on ubuntu (11.04) and am having problems with x264.
I got x264 last version from git and its configure gave me this:
```
platform:      X86_64
system:        LINUX
cli:           yes
libx264:       internal
shared:        no
static:        no
asm:           yes
interlaced:    yes
avs:           no
lavf:          yes
ffms:          no
gpac:          yes
gpl:           yes
thread:        posix
filters:       resize crop select_every 
debug:         no
gprof:         no
strip:         no
PIC:           no
visualize:     no
bit depth:     8
chroma format: all

You can run 'make' or 'make fprofiled' now.
```

After compiling and installing I get this from "x264 --version":
```
x264 0.120.2164 da19765
(libswscale 2.1.100)
(libavformat 54.1.100)
built on Feb 21 2012, gcc: 4.5.2
configuration: --bit-depth=8 --chroma-format=all
x264 license: GPL version 2 or later
libswscale/libavformat license: LGPL version 2.1 or later

```

The problem is that neither [ffmpeg](http://www.videohelp.com/tools/ffmpeg) or [mplayer](http://www.videohelp.com/tools/MPlayer) seem to find this library installed. Both configure scripts say no even when trying --enable-libx264 (ffmpeg simply say I don't have x264 >= 118).

Other things I found out are that ffmpeg detects everything BUT the encoding features for h264 and my videos with this codec do play fine ([VLC Media Player](http://www.videohelp.com/tools/VLC-media-player) apparently is even using the x264 library itself). Also when I run the version.sh script after installing it gives me this:

```
#define X264_REV 2164
#define X264_REV_DIFF 0
#define X264_VERSION " r2164 da19765"
#define X264_POINTVER "0.120.2164 da19765"

```



Some extra that can be useful:

[list][ffmpeg's config.log](http://codepad.org/KWQ0pbDs) pastebin[/list][list][mplayer's config.log](http://codepad.org/EWvhUCUq) pastebin[/list]

Thank you for your attention...

---

### Post by FakeOutdoorsman on 2012-02-22
You probably forgot to add *--enable-static* to your x264 configure, and the FFmpeg configure requires *--enable-gpl --enable-libx264*. For step-by-step instructions see:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)
[Howto: Build the svn MPlayer under the latest release version of Ubuntu](http://ubuntuforums.org/showthread.php?t=1542240)

---

### Post by rzippert on 2012-02-24
Well... I tried to enable static and it begun to be detected, but then I got problems when the compiler got to libx264.

I don't really understand why, but following the steps on the guide compiling works... Gonna find out later...

Thanks for your help... Really appreciated.

---

