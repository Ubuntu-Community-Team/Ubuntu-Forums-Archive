---
title: "Fuppes gives --enable-video-transcoding error"
date: 2010-08-21
forum: General Help
---

### Post by baklap on 2010-08-21
Hey,

When I try to configure fuppes on ubuntu server 10.04 I get the following error, and I am not able to get transcoding to work.

When I run:
```
./configure --enable-video-transcoding
```I get the following output:
```
configure: WARNING: unrecognized options: --enable-video-transcoding
```The fupper serverconfig output says this:
```
CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : enabled  (Wand C-API)

  audio metadata extraction plugins
    taglib             : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : enabled
    ImageMagick        : enabled  (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  database plugins
    mysql              : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : enabled
    inotify            : enabled
```There is no video transcoding support in this build. I can't get it to work and I'm getting totally freaked out because there are no search results on google on this error.

Is there anybody who recognizes this problem or has a single clue how to solve this?

Audio is running like a charm but I'm only able to run video on my ps3 which is not transcoded. My tv needs transcoded data and that's whats not working.

Thanks in advance.

EDIT:
Screw me, already got it.

```
./configure \
--prefix=/usr \
--enable-faad \
--enable-lame \
--enable-mad \
--enable-transcoder-ffmpeg \
--enable-twolame \
--disable-ffmpegthumbnailer
```

---

### Post by w4itey on 2010-11-20
Wanted to say thanks had the same problem your fix worked like a charm

---

