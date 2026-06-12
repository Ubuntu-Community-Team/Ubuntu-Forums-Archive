---
title: "FFMPEG encoding presets aren't working"
date: 2012-03-12
forum: General Help
---

### Post by J V on 2012-03-12
The ffmpeg presets which didn't come with the package in xubuntu precise aren't working from my ~/.ffmpeg directory.

```
$ ls ~/.ffmpeg
libx264-lossless_ultrafast.ffpreset

$ ffmpeg -f alsa -i pulse -f x11grab -r 10 -s hd720 -i :0.0+320,180 -vcodec libx264 -vpre lossless_ultrafast -acodec libmp3lame -threads 1 -y -sameq
ffmpeg version 0.8-4:0.8-1ubuntu2, Copyright (c) 2000-2011 the Libav developers
  built on Feb  9 2012 08:03:03 with gcc 4.6.2
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
[alsa @ 0x1f219c0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x1f219c0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1331592385.315708, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x1f221e0] device: :0.0+320,180 -> display: :0.0 x: 320 y: 180 width: 1280 height: 720
[x11grab @ 0x1f221e0] shared memory extension  found
[x11grab @ 0x1f221e0] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0+320,180':
  Duration: N/A, start: 1331592385.420240, bitrate: 294912 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1280x720, 294912 kb/s, 10 tbr, 1000k tbn, 10 tbc
File for preset 'lossless_ultrafast' not found

$ ffmpeg
ffmpeg version 0.8-4:0.8-1ubuntu2, Copyright (c) 2000-2011 the Libav developers
  built on Feb  9 2012 08:03:03 with gcc 4.6.2
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

```

Edit: I just saw this is now deprecated, how should I use avconv to capture from my desktop?

---

### Post by ron999 on 2012-03-12
...

---

