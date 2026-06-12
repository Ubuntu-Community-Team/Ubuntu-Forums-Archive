---
title: "dvd:rip can't write .pm file"
date: 2006-03-01
forum: General Help
---

### Post by jigantor on 2006-03-01
Pretty much the last thing I have yet to figure out on Breezy, I want to rip DVDs and encode them in AVI format. dvd:rip rips them without a problem, but when I go to transcode them it gives me a message like this:

An internal exception was thrown!
The error message was:

can't write /home/tim/dvdrip/StarTrekSeason3-2/avi/001/StarTrekSeason3-2-001.dvdrip-info at /usr/share/perl5/Video/DVDRip/InfoFile.pm line 265

My first (and indeed only) thought was that somehow InfoFile.pm was read-only when it shouldn't have been, but that seems not to be the case. If anyone has any bright ideas they'd be much appreciated!

---

### Post by schilcha on 2006-03-01
[QUOTE=jigantor]
can't write /home/tim/dvdrip/StarTrekSeason3-2/avi/001/StarTrekSeason3-2-001.dvdrip-info at /usr/share/perl5/Video/DVDRip/InfoFile.pm line 265
[/QUOTE]
Tries to say that, while running through the program an error occurred. The part of the program that encountered that error can be found in the file InfoFile.pm at line 265 -- there's no need for write-access to that file. What you need write access for is the directory /home/tim/dvdrip/StarTrekSeason3-2/avi/001/ and the file StarTrekSeason3-2-001.dvdrip-info there (if it already exists).

Make sure the directory /home/tim/.../001/ direcotry exsist, that you can enter it and create a (empty) file there. Also, check if your disk is full.

Good Luck!

---

### Post by jigantor on 2006-03-03
As it turned out, during a previous experiemnt I had inadvertently made that directory (and a few others) read-only. However, I've now run into a new problem:
[FONT="Courier New"]
Job 'Transcoding Video - title #1, pass 1' failed.[/FONT]

(...)

[FONT="Courier New"]
Last output was:

transcode v 1.0.1 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg

libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Couldn't find device name.
libdvdread: Can't open file VIDEO_TS.IFO
tc_memcpy: using sse for memcpy
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PC/M | (subtitle)

[transcode] warning: /usr/lib/transcode/export_divx4.so: cannot open shared object file: No such file or directory
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0ms | 0 ms
[transcode] auto-probing source /home/tim/dvdrip/NobleRegentsPark/vob/001 (ok)
[transcode] V: import format (MPEG-2) (V=vob|A=null)
[transcode] V: AV demux/sync | (1) sync AV at initial MPEG sequence
[transcode] V: import frame | 720x576 1.25:1 encoded @ 16.9
[transcode] V: new aspect ration | 640x360 1.78:1 (-B)
[transcode] V: clip frame (->) |  640x360
[transcode] V: bits/pixel |  0.233
[transcode] V: decoding fps, frc | 25.000,0
[transcode] V: multi-pass | (mode= 1) writing data (pass 1) to divx4.log
[transcode] V: Y'CbCr | YV 12/1420
[transcode] A: import format |0x2000 AC3     [48000,16,2]  192 kbps
[transcode] A: export | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per fram | 7860 (7860.000000)
[transcode] A: adjustment | 0@ 1000
[transcode] A: rescale stream | 2.910
[transcode] V: IA32/AMD64 accel | sse (sse 3dnowext 3dnow mmxext mmx asm C)
[transcode] V: video buffer | 10 @ 720x576
[transcode] warning: (dl_loader.c) loading /usr/lib/transcode/exportdivx4.so failed
[transcode] warning: (encoder.c) loading video export module failed
[transcode] warning: failed to init export modules
[transcode] critical: plug-in initialisation failed[/FONT]

---

### Post by Ikitt on 2006-03-04
Hi,

[QUOTE=jigantor]
[...]
[transcode] warning: /usr/lib/transcode/export_divx4.so: cannot open shared object file: No such file or directory
[...][/quote]
This transcode installation lacks `divx4' export plugin. This is right, since divx4 is ancient and poorly supported (by transcode and generally speaking outside windows world). Try using a different export plugin, like `xvid4' or `ffmpeg'.

---

