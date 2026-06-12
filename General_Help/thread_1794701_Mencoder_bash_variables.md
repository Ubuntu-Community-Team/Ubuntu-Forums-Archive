---
title: "Mencoder bash variables"
date: 2011-07-01
forum: General Help
---

### Post by jaes84 on 2011-07-01
I am trying to run mencoder to create a movie out of jpg files in a script, but however i get this error whenever i run it:
```

MEncoder 2:1.0~rc2-0ubuntu13.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Xeon(TM) CPU 3.00GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing command line)

```

Here is the relevant code i am trying to run
```

avi_name="$(date +%H).avi"
mencoder mf://*.jpg -mf w=640:h=480:fps=24:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o $avi_name

```

---

### Post by nothingspecial on 2011-07-01
Have you tried quoting your variable?

[http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

---

### Post by jaes84 on 2011-07-01
> **nothingspecial said:**
> Have you tried quoting your variable?

[http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

Yes, that makes no diffrence

---

### Post by nothingspecial on 2011-07-01
hmmmm, no errors here, just tried it, albeit with 12 images


```
mencoder mf://*.jpg -mf w=640:h=480:fps=24:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o $avi_name
MEncoder 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
[mf] number of files: 12 (48)
VIDEO:  [IJPG]  640x480  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:640x480  fps:24.000  ftime:=0.0417
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect.
[swscaler @ 0x908c2d0]BICUBIC scaler, from yuv422p to yuv420p using MMX2
videocodec: libavcodec (1680x1050 fourcc=34504d46 [FMP4])
[VE_LAVC] High quality encoding selected (non-realtime)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect..000 [0:0]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect..000 [0:0]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect..000 [0:0]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect..000 [0:0]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect..000 [0:0]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect..000 [0:0]
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect.0.000 [0:0]
Pos:   0.5s     12f (100%)  2.50fps Trem:   0min   0mb  A-V:0.000 [0:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 16535.328 kbit/s  (2066916 B/s)  size: 1033458 bytes  0.500 secs  12 frames
```

---

### Post by jaes84 on 2011-07-01
Hmm, mind posting that exact script please ?

---

### Post by nothingspecial on 2011-07-01
> **jaes84 said:**
> Hmm, mind posting that exact script please ?

Ah, sorry. I didn't notice this was just part of a script. I just ran those 2 lines.


..perhaps you should post your script :)

---

### Post by jaes84 on 2011-07-01
Wow, a simple rouge shopt broke it. anyway, i now get this error
```

mencoder mf://*.jpg -mf w=640:h=480:fps=24:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o "$avi_name"
MEncoder 2:1.0~rc2-0ubuntu13.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Xeon(TM) CPU 3.00GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


```

---

### Post by jaes84 on 2011-07-01
> **nothingspecial said:**
> Ah, sorry. I didn't notice this was just part of a script. I just ran those 2 lines.


..perhaps you should post your script :)

Never mind, it was basically my script.

---

### Post by nothingspecial on 2011-07-01
Read the bash pitfalls link I posted. It cleared up a lot of my bad scripting habits. :P

---

### Post by jaes84 on 2011-07-01
Thanks for your help, turns out a file was in the directory that wasnt a jpg, and for some reason that messed it up. Thanks alot

---

