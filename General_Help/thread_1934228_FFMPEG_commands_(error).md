---
title: "FFMPEG commands (error)"
date: 2012-03-01
forum: General Help
---

### Post by Vigh on 2012-03-01
How do I render these images in HD1080p. Regards. Ant.

Original Command

ffmpeg -f image2 -i /home/anthony/newton/newton4%04d.png -r 30 -s 1920x1080 /home/anthony/Desktop/newton4.mkv 


Terminal Ouput

ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
Input #0, image2, from '/home/anthony/newton/newton4%04d.png':
  Duration: 00:00:00.08, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, rgb24, 1920x1080, 25 tbr, 25 tbn, 25 tbc
[COLOR="Green"]Incompatible pixel format 'rgb24' for codec 'mpeg4', auto-selecting format 'yuv420p'[/COLOR]
[buffer @ 0x8fdff60] w:1920 h:1080 pixfmt:rgb24
[ffsink @ 0x8fe8380] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x8fe6b80] w:1920 h:1080 fmt:rgb24 -> w:1920 h:1080 fmt:yuv420p flags:0x4
Output #0, matroska, to '/home/anthony/Desktop/newton4.mkv':
  Metadata:
    encoder         : Lavf53.3.0
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1080, q=2-31, 200 kb/s, 1k tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
frame=    2 fps=  0 q=2.0 Lsize=     398kB time=0.07 bitrate=48668.2kbits/s    
video:397kB audio:0kB global headers:0kB muxing overhead 0.138810%

---

### Post by Vigh on 2012-03-01
Different error now. Getting closer to success, just getting some buffer under-runs now. Anyone know how to fix this?

Original Command
ffmpeg -f image2 -i /home/anthony/newton-JPG/newton4%04d.jpg -r 30 -s 1920x1080 -sameq -bufsize 18395 /home/anthony/Desktop/newton4.vob 

ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1+medibuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1+medibuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
Input #0, image2, from '/home/anthony/newton-JPG/newton4%04d.jpg':
  Duration: 00:00:00.08, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 1920x1080 [PAR 1:1 DAR 16:9], 25 tbr, 25 tbn, 25 tbc
File '/home/anthony/Desktop/newton4.vob' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'yuvj420p' for codec 'mpeg2video', auto-selecting format 'yuv420p'
[buffer @ 0x9955bc0] w:1920 h:1080 pixfmt:yuvj420p
[ffsink @ 0x9955c80] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x995b760] w:1920 h:1080 fmt:yuvj420p -> w:1920 h:1080 fmt:yuv420p flags:0x4
Output #0, svcd, to '/home/anthony/Desktop/newton4.vob':
  Metadata:
    encoder         : Lavf53.3.0
    Stream #0.0: Video: mpeg2video, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
[COLOR="DarkRed"][mpeg2video @ 0x9956460] rc buffer underflow
[svcd @ 0x9955d60] buffer underflow i=0 bufi=8083 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=8083 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=10107 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=10107 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=12131 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=12131 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=14155 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=14155 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=16179 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=16179 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=18203 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=18203 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=20227 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=20227 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=22251 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=22251 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=24275 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=24275 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=26299 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=26299 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=28323 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=28323 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=30347 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=30347 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=32371 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=32371 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=34395 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=34395 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=36419 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=36419 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=38443 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=38443 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=40467 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=40467 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=42491 size=45785
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=42491 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=44515 size=45785
[mpeg2video @ 0x9956460] rc buffer underflow
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=44515 size=45785
[svcd @ 0x9955d60] buffer underflow i=0 bufi=6816 size=18395
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=6816 size=18395
[svcd @ 0x9955d60] buffer underflow i=0 bufi=8840 size=18395
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=8840 size=18395
[svcd @ 0x9955d60] buffer underflow i=0 bufi=10864 size=18395
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=10864 size=18395
[svcd @ 0x9955d60] buffer underflow i=0 bufi=12888 size=18395
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=12888 size=18395
[svcd @ 0x9955d60] buffer underflow i=0 bufi=14912 size=18395
[svcd @ 0x9955d60] packet too large, ignoring buffer limits to mux it
[svcd @ 0x9955d60] buffer underflow i=0 bufi=14912 size=18395
[svcd @ 0x9955d60] buffer underflow i=0 bufi=16936 size=18395
packet too large, ignoring buffer limits to mux it03 bitrate=15728.6kbits/s    
[svcd @ 0x9955d60] buffer underflow i=0 bufi=16936 size=18395
frame=    2 fps=  2 q=31.0 Lsize=      66kB time=0.03 bitrate=16220.2kbits/s    
video:63kB audio:0kB global headers:0kB muxing overhead 5.303833%[/COLOR]
anthony@steve-buntu:~/newton-JPG$

---

### Post by Vigh on 2012-03-06
bump

---

### Post by FakeOutdoorsman on 2012-03-07
Both commands should have provided an output file. I only see notifications or warnings, but not any important errors that would have stopped the encoding.

I don't recommend usage of the *-sameq* option; it does not mean same quality as the documentation used to imply. Use *-qscale* instead to control quality. When using the mpeg2video or mpeg4 encoders (as your two examples are) values of 2-5 should suffice with a lower value being higher quality. Your input is already 1920x1080 so you don't need to declare it as an output option. You should move -r as an input option. Currently ffmpeg is decoding your input as 25 fps and outputting as 30 fps. Moving it as an input option will allow it to do both at 30 fps which I assume is what you want.

```
ffmpeg -r 30 -i /home/anthony/newton-JPG/newton4%04d.jpg -qscale 3 output.mkv
```

---

