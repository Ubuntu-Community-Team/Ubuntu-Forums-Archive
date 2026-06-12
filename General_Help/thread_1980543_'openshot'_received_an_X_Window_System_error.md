---
title: "'openshot' received an X Window System error"
date: 2012-05-15
forum: General Help
---

### Post by linuxcss on 2012-05-15
running xubuntu 11.10, tried both openshot 1.4.0 and 1.4.2

during the course of resizing the preview window can make 1.4.0 and 1.4.2 versions of openshot crash and then trying to restart openshot I get the following (below)
and only way I know how to recover and a real pain is to logout and login again:

admin1@cw200x4-main:~$ openshot

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------
Process no longer exists: 21629.  Creating new pid lock file.

Detecting formats, codecs, and filters...
---
video_codecs:
  - a64multi
  - a64multi5
  - asv1
  - asv2
  - bmp
  - dnxhd
  - dpx
  - dvvideo
  - ffv1
  - ffvhuff
  - flashsv
  - flv
  - gif
  - h261
  - h263
  - h263p
  - huffyuv
  - jpegls
  - ljpeg
  - mjpeg
  - mpeg1video
  - mpeg2video
  - mpeg4
  - msmpeg4v2
  - msmpeg4
  - pam
  - pbm
  - pcx
  - pgm
  - pgmyuv
  - png
  - ppm
  - qtrle
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - snow
  - svq1
  - targa
  - tiff
  - v210
  - wmv1
  - wmv2
  - zlib
  - zmbv
  - libschroedinger
  - libtheora
  - libvpx
...
---
audio_codecs:
  - aac
  - ac3
  - ac3_fixed
  - alac
  - eac3
  - flac
  - mp2
  - nellymoser
  - real_144
  - vorbis
  - wmav1
  - wmav2
  - pcm_alaw
  - pcm_f32be
  - pcm_f32le
  - pcm_f64be
  - pcm_f64le
  - pcm_mulaw
  - pcm_s8
  - pcm_s16be
  - pcm_s16le
  - pcm_s24be
  - pcm_s24daud
  - pcm_s24le
  - pcm_s32be
  - pcm_s32le
  - pcm_u8
  - pcm_u16be
  - pcm_u16le
  - pcm_u24be
  - pcm_u24le
  - pcm_u32be
  - pcm_u32le
  - pcm_zork
  - roq_dpcm
  - adpcm_adx
  - g722
  - g726
  - adpcm_ima_qt
  - adpcm_ima_wav
  - adpcm_ms
  - adpcm_swf
  - adpcm_yamaha
  - libgsm
  - libgsm_ms
  - libvorbis
...
---
formats:
  - a64
  - ac3
  - adts
  - aiff
  - amr
  - asf
  - ***
  - asf_stream
  - au
  - avi
  - avm2
  - cavsvideo
  - crc
  - daud
  - dirac
  - dnxhd
  - dts
  - dv
  - eac3
  - ffm
  - ffmetadata
  - filmstrip
  - flac
  - flv
  - framecrc
  - framemd5
  - g722
  - gif
  - gxf
  - h261
  - h263
  - h264
  - image2
  - image2pipe
  - ipod
  - ivf
  - m4v
  - md5
  - matroska
  - matroska
  - mjpeg
  - mlp
  - mmf
  - mov
  - mp2
  - mp3
  - mp4
  - mpeg
  - vcd
  - mpeg1video
  - dvd
  - svcd
  - mpeg2video
  - vob
  - mpegts
  - mpjpeg
  - mxf
  - mxf_d10
  - null
  - nut
  - ogg
  - alaw
  - mulaw
  - f64be
  - f64le
  - f32be
  - f32le
  - s32be
  - s32le
  - s24be
  - s24le
  - s16be
  - s16le
  - s8
  - u32be
  - u32le
  - u24be
  - u24le
  - u16be
  - u16le
  - u8
  - psp
  - rawvideo
  - rm
  - RoQ
  - rso
  - rtp
  - rtsp
  - sap
  - sox
  - spdif
  - srt
  - swf
  - 3g2
  - 3gp
  - truehd
  - rcv
  - voc
  - wav
  - webm
  - yuv4mpegpipe
  - alsa
  - oss
...
state saved
The program 'openshot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 25 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

