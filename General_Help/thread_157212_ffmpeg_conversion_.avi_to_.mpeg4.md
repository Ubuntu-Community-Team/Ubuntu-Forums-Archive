---
title: "ffmpeg conversion: .avi to .mpeg4"
date: 2006-04-08
forum: General Help
---

### Post by limaunion on 2006-04-08
Hi all!
I'm trying to convert my .avi videos taken from a Canon Powershot camera to mpeg4 format.

I'm getting this error, any ideas? otherwise which other options do I have (examples) ? 
Thanks!.

$ ffmpeg -i mvi_4269.avi -vn -vcodec mpeg4 -acodec ac3 outfile.mpg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, avi, from 'mvi_4269.avi':
  Duration: 00:00:30.0, start: 0.000000, bitrate: 7092 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 15.00 fps
  Stream #0.1: Audio: pcm_u8, 11024 Hz, mono, 88 kb/s
Output #0, mpeg, to 'outfile.mpg':
  Stream #0.0: Audio: ac3, 11024 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by francisco_athens on 2006-05-28
I use Avidemux to convert my powershot AVIs in Dapper (6.06).
this is how I do it using Xvid+Lame codecs:
you'll need to enable "multiverse" repositories for Avidemux, Xvid and Lame libraries

open video
set video compressor to Xvid or you can use whatever other codec like Mpeg4(lavc) works nicely too..
configure video two-pass and calculate target filesize between 2-5MB/minute
set audio to Audio compressor to Lame (or ffmAC3, or whatever) 
set audio "filters" to Resample to hz 22050 (otherwise Lame and other codecs may not initialize!!)

save video

---

