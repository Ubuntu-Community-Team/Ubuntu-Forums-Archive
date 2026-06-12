---
title: "Unable to play media in Subsonic webapp"
date: 2011-11-14
forum: General Help
---

### Post by Weidbrewer on 2011-11-14
I use the service [Subsonic]("http://www.subsonic.org/pages/index.jsp") to stream music to my Android phone, and to view my videos remotely.  This past week, it ceased working in the webapp.  I can still stream music to both my phone, and the Perisonic Chrome app, but if I navigate to my server's URL, I can't play anything.

I can *access* the site, and everything is there, but none of the playing options work, except clicking the "share" link for music.  When I click "play" on a music file, nothing happens, and nothing shows in the log.  When I click play on a video, the normal webplayer comes up, but displays a string of error text.  My log after trying both music and then a video file looks like:

```
    [2011-11-11 20:34:48,588] INFO DaoHelper - Checking database schema.
    [2011-11-11 20:34:49,256] INFO DaoHelper - Done checking database schema.
    [2011-11-11 20:34:49,559] INFO SearchService - Automatic index creation scheduled to run every 1 day(s), starting at Sat Nov 12 03:00:00 EST 2011
    [2011-11-11 20:34:49,785] INFO PodcastService - Automatic Podcast update scheduled to run every 24 hour(s), starting at Fri Nov 11 20:39:49 EST 2011
    [2011-11-11 20:34:53,053] INFO VersionService - Resolved local Subsonic version to: 4.5
    [2011-11-11 20:34:53,203] INFO VersionService - Resolved latest Subsonic final version to: 4.5
    [2011-11-11 20:34:53,205] INFO VersionService - Resolved latest Subsonic beta version to: 4.6.beta1
    [2011-11-11 20:34:54,490] INFO NetworkService - Successfully forwarding port 4040.
    [2011-11-11 20:35:04,128] INFO PlaylistInputStream - admin listening to "Already Aired/Boardwalk.Empire.S02E07.HDTV.XviD-ASAP.avi"
    [2011-11-11 20:35:04,161] DEBUG TranscodeInputStream - Starting transcoder: [/var/subsonic/transcode/ffmpeg] [-ss] [0] [-i] [/media/raid/videos/Already Aired/Boardwalk.Empire.S02E07.HDTV.XviD-ASAP.avi] [-async] [1] [-b] [1000k] [-s] [624x352] [-ar] [44100] [-ac] [2] [-v] [0] [-f] [flv] [-]
    [2011-11-11 20:35:04,184] DEBUG TranscodeInputStream - Starting transcoder: [/var/subsonic/transcode/lame] [-b] [1000] [--tt] [Boardwalk.Empire.S02E07.HDTV.XviD-ASAP] [--t]
    [2011-11-11 20:35:04,203] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg) FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   configuration: --extra-version=4:0.5.1-1ubuntu1.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libavutil     49.15. 0 / 49.15. 0
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libavcodec    52.20. 1 / 52.20. 1
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libavformat   52.31. 0 / 52.31. 0
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libavdevice   52. 1. 0 / 52. 1. 0
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libavfilter    0. 4. 0 /  0. 4. 0
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libswscale     0. 7. 1 /  0. 7. 1
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   libpostproc   51. 2. 0 / 51. 2. 0
    [2011-11-11 20:35:04,204] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   built on Sep 16 2011 17:08:44, gcc: 4.4.3
    [2011-11-11 20:35:04,230] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/lame) /var/subsonic/transcode/lame: unrecognized option --t
    [2011-11-11 20:35:04,333] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg) Input #0, avi, from '/media/raid/videos/Already Aired/Boardwalk.Empire.S02E07.HDTV.XviD-ASAP.avi':
    [2011-11-11 20:35:04,333] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   Duration: 00:59:24.28, start: 0.000000, bitrate: 1293 kb/s
    [2011-11-11 20:35:04,333] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)     Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    [2011-11-11 20:35:04,333] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)     Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
    [2011-11-11 20:35:04,337] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg) Stream mapping:
    [2011-11-11 20:35:04,338] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   Stream #0.0 -> #0.0
    [2011-11-11 20:35:04,338] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg)   Stream #0.1 -> #0.1
    [2011-11-11 20:35:04,355] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg) Press [q] to stop encoding
    [2011-11-11 20:35:04,404] DEBUG InputStreamReaderThread - (/var/subsonic/transcode/ffmpeg) av_interleaved_write_frame(): Error while opening file


```

I have verified that I am using the webplayer and that the decoders are installed in the proper location.  Again, I can access music with external music streamers, but cannot access anything in the webapp itself.  

Ubuntu 10.04, 64-bit, fully updated.

Any advice would be greatly appreciated.

---

