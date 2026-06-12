---
title: "install kubuntu-restricted-extras without openjdk"
date: 2010-06-24
forum: General Help
---

### Post by jepong on 2010-06-24
Hello... i want to install kubuntu-restricted-extras but i prefer sun-java6 packages over openjdk... how can i exclude openjdk from installing when i install kubuntu-restricted-extras.

Thanks!

---

### Post by Zorael on 2010-06-24
You could separately install the packages that kubuntu-restricted-extras installs.
```
$ sudo aptitude install flashplugin-installer icedtea6-plugin libavcodec-extra-52 libk3b6-extracodecs libmp3lame0 libtunepimp5-mp3 libxine1-ffmpeg ttf-mscorefonts-installer unrar --without-recommends
```

Alternatively let it install OpenJDK along with everything else, and then uninstall OpenJDK afterwards.

---

### Post by jepong on 2010-06-25
thanks... this my workadound too... and i don't install icedtea6-plugin.

---

