---
title: "Error when compiling VLC"
date: 2006-03-20
forum: General Help
---

### Post by wr0x2 on 2006-03-20
I'm compiling my own version of VLC with matroska support enabled. I had to install a couple things during the configure, but finally I got that script to run successfully and I did a "sudo make."

Everything goes fine until...

```

Making all in ffmpeg
make[5]: Entering directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules/codec/ffmpeg'
make[6]: Entering directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules/codec/ffmpeg'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../..   -DSYS_LINUX -I../../../include `top_builddir="../../.." ../../../vlc-config --cflags plugin ffmpeg` -Wsign-compare -Wall  -pipe -MT libffmpeg_plugin_a-ffmpeg.o -MD -MP -MF ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" -c -o libffmpeg_plugin_a-ffmpeg.o `test -f 'ffmpeg.c' || echo './'`ffmpeg.c; \
then mv -f ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" ".deps/libffmpeg_plugin_a-ffmpeg.Po"; else rm -f ".deps/libffmpeg_plugin_a-ffmpeg.Tpo"; exit 1; fi
ffmpeg.c:49:44: error: libpostproc/postprocess.h: No such file or directory
make[6]: *** [libffmpeg_plugin_a-ffmpeg.o] Error 1
make[6]: Leaving directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/wr0x2/Desktop/vlc-0.8.4a/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wr0x2/Desktop/vlc-0.8.4a'
make: *** [all] Error 2
wr0x2@USSENTERPRISE:~/Desktop/vlc-0.8.4a$ f

```

Any idea what's going on here? It messes up while making ffmpeg...

---

### Post by wr0x2 on 2006-03-20
Problem solved, but even using --enable-mkv in ./config VLC won't play MKV files. It plays all other kinds of files I have though.

---

### Post by wr0x2 on 2006-03-20
Mplayer reports the video portion of the file as being encoded with h264. Mplayer will play the file, but it's extremely offsync so I choose not to use it. Can I drop my mplayer codecs off in VLC's codec folder?

---

