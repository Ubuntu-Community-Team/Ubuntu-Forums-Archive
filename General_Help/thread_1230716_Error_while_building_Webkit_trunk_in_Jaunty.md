---
title: "Error while building Webkit trunk in Jaunty"
date: 2009-08-03
forum: General Help
---

### Post by lviggiani on 2009-08-03
Hi guys,
I'm trying to build latest Webkit from svn.
I've installed all possible dependencies comprising libphonon-dev but I still get the following error while running
```
$ QTDIR=/usr/share/qt4/ WebKit/WebKitTools/Scripts/build-webkit

```

```
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.cpp:40:30: error: Phonon/AudioOutput: No such file or directory
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.cpp:41:30: error: Phonon/MediaObject: No such file or directory
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.cpp:42:30: error: Phonon/VideoWidget: No such file or directory
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.cpp: In function ‘QByteArray debugMediaObject(WebCore::MediaPlayerPrivate*, const Phonon::MediaObject&)’:
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.cpp:57: error: invalid use of incomplete type ‘const struct Phonon::MediaObject’
../../../WebCore/platform/graphics/qt/MediaPlayerPrivatePhonon.h:34: error: forward declaration of ‘const struct Phonon::MediaObject’
...and so on...
```
To me it looks like I miss some dependency but I can't figure out what exactly do I miss...
Thanks in advance for any help!

---

