---
title: "Fuppes and taglib disabled"
date: 2009-09-29
forum: General Help
---

### Post by teropita on 2009-09-29
I have fuppes up and running but cannot get taglib enabled.

I have configured with --enable-taglib and without as it is default yes anyway.

The configure output shows 

check optional stuff

checking for taglib-config... no
checking for IMAGEMAGICK_WAND... no
checking for EXIV2... no
checking for LIBAVFORMAT... yes

I have /usr/bin/taglib-config

and the list of enabled disabled includes

 video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Wand C-API)

  audio metadata extraction plugins
    taglib        : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : disabled (mp4/m4a)



Any idea how I can fix this problem?


Thanks in advance.

---

### Post by teropita on 2009-09-30
I found that I had to configure with the --prefix=/usr option.

but then I found I had to uninstall completely delete the install directory download the install and start from scratch before fuppes would work again.

---

