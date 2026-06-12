---
title: "Sending open data stream from one computer to another"
date: 2010-05-24
forum: General Help
---

### Post by NimbleRabit on 2010-05-24
I'm trying to use a program called GLC to capture my games video to eventually be streamed online.  I was able to get my computer to capture the video and encode it on the fly using this setup:

```
mkfifo fifo.glc
glc-capture -b back -o fifo.glc -s -f 15 -r 0.5 --disable-audio $@ &
glc-play fifo.glc -y 1 -o - | mencoder -demuxer y4m -nosound - -ovc lavc -o gl-capture.mpeg
```

Basically I create a named pipe, output the raw video data into it, and then I use GLC's command + mencoder to read from the pipe and output a fully encoded video.

That works fine on my computer, but now I want to try to offload the encoding to another computer and I'm stuck.  Here's the method I came up with which does not work:

```
glc-capture -s -f 15 -r 0.5 --disable-audio -o /dev/stdout ./hon-x86_64 | nc 192.168.0.7 6800
```

That runs on my main computer (where the video is being captured), and outputs the raw video data to my server (at least that's what I'm hoping it does).

```
nc -l -p 6800 | tee -a fifo.glc

glc-play fifo.glc -y 1 -o - | mencoder -demuxer y4m -nosound - -ovc lavc -o gl-capture.mpeg
```

I then run both of these commands on the server, theoretically outputting the raw video data into a named pipe (once again, but now on the server), and then using GLC's command + mencoder to read from the pipe and output a fully encoded video.  Except this doesn't work, and I don't know why.  Here's the mencoder output:

```
MEncoder SVN-r29978-4.4.1 (C) 2000-2009 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
Reading from stdin...
success: format: 0  data: 0x0 - 0x0
[  11.90s       file error ] Bad message (74)
exporting yuv4mpeg failed: Bad message (74)
YUV4MPEG2 file format detected.
YUV4MPEG2 Video stream 0 size: display: 840x524, codec: 840x524
VIDEO:  [YV12]  840x524  12bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:12  fourcc:0x32315659  size:840x524  fps:15.000  ftime:=0.0667
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 840 x 524 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (840x524 fourcc=34504d46 [FMP4])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:      nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  0 frames
```

---

