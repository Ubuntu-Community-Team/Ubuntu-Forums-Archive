---
title: "Any way to install wmv/h264 codecs without using restricted format package?"
date: 2010-07-27
forum: General Help
---

### Post by culfunius on 2010-07-27
I really don't want to have to install the microsoft fonts or Java. So can wmv and h264 codecs be installed separately, and if so, how?

---

### Post by Vaphell on 2010-07-27
```
apt-cache depends ubuntu-restricted-extras

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
ttf-mscorefonts-installer
flashplugin-installer
unrar
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
libavcodec-extra-52
icedtea6-plugin
libmp4v2-0

```

install the ones you need

---

### Post by culfunius on 2010-07-27
That's exactly what I needed - cheers!

---

