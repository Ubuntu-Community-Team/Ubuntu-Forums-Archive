---
title: "Messed up /usr/lib"
date: 2010-03-14
forum: General Help
---

### Post by Granknight on 2010-03-14
i mistakenly replaced several libraries from /usr/lib with those from another os; this leading me to alot of applications not running such as apt-get , gnome-system-monitor , amarok and many other. the libraries i replaced are:
```
libavcodec.so   libcrypto.so.0.9.8   libgtk-1.2.so.0  libopenal.so.1         libssl.so.0.9.8     libvorbis.so.0
libavformat.so  libgdk-1.2.so.0      libjpeg.so.62    libSDL-1.2.so.0        libstdc++.so.6
libavutil.so    libgmodule-1.2.so.0  libogg.so.0      libSDL_mixer-1.2.so.0  libvorbisfile.so.3
```
is there a way to restore or replace them with original/working ones? without reinstalling the whole OS?
I could not do anything with apt-get/aptitude because they're not working, but if needed i have the disk i used to install the system.
I'm using ubuntu karmic 32bit.

---

### Post by Granknight on 2010-03-14
I think i got further into it... the problem comes from library libstdc++.so.6 / libstdc++.so.13 and i need a way to restore it...
can i copy it from another updated ubuntu karmic to use it on mine?
if not, is there a way to download it from internet?

another thing... now ubuntu can't mount my kingston drive, sees but can' t mount. previously it could mount it, even after the problem happened. what's wrong with it?

---

