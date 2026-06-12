---
title: "Use 'apt-get autoremove' to remove them."
date: 2012-04-23
forum: General Help
---

### Post by eival on 2012-04-23
is there anything that could possibly go wrong from running this?

is there a possibility the system removes something important?


```
The following packages were automatically installed and are no longer required:
  libopenal1 libmarble4 libclucene0ldbl menu libprocessui4 ttf-umefont
  libtaskmanager4 libksane0 libavutil49 libpackagekit-glib2-12
  libkscreensaver5 libsolidcontrolifaces4 libxine1-x libbluray0 libsvga1
  oxygen-icon-theme libboost-program-options1.40.0
  gstreamer0.10-plugins-ugly-multiverse kdebase-data kdelibs5
  libqt4-qt3support shared-desktop-ontologies kdebase-workspace-libs4+5
  gstreamer0.10-plugins-bad-multiverse libplasma-geolocation-interface4
  libxine1-bin libexiv2-6 odbcinst libpackagekit-qt-12 wwwconfig-common
  unixodbc libakonadiprivate1 libx264-85 libsoprano4 libpolkit-qt-1-0
  libksgrd4 libkworkspace4 kdelibs5-data libdbusmenu-qt2 odbcinst1debian1
  libkfontinst4 libxcb-shape0 icoutils ttf-symbol-replacement
  python-packagekit libstreamanalyzer0 packagekit libkephal4 libplasma3
  ttf-dejavu libplasmaclock4 kdepimlibs5 libweather-ion4 kdelibs-bin
  libsolidcontrol4 libattica0 libqt4-phonon libvdpau1 libkonq5-templates
  libmpg123-0 libffmpegthumbnailer4 javascript-common libksignalplotter4
  libstreams0 packagekit-backend-apt exiv2 liblsofui4 libjs-prototype
  marble-data libplasma-applet-system-monitor4 libssh-4 virtuoso-nepomuk
  soprano-daemon libprocesscore4 kdebase-runtime-data libebml0 libiodbc2
  kdepimlibs-data libmatroska0 libiptcdata0 ttf-droid libxine1-console

```

---

### Post by cortman on 2012-04-23
It looks as though it's removing a lot of KDE/QT stuff- Did you have KDE installed at one point and remove it?
If so, I don't see any harm coming of it. apt-get autoremove is generally pretty trustworthy.

---

### Post by eival on 2012-04-23
> **cortman said:**
> It looks as though it's removing a lot of KDE/QT stuff- Did you have KDE installed at one point and remove it?
If so, I don't see any harm coming of it. apt-get autoremove is generally pretty trustworthy.

yeah probably, i use 10.04 since release, so i cant remember all that i added/removed over the last 2+years

but basically i just wanted to make sure nothing system necessary would be removed, worse case if something i run needs it-it would just prompt me to reinstall it right?

---

### Post by cortman on 2012-04-23
> **eival said:**
> yeah probably, i use 10.04 since release, so i cant remember all that i added/removed over the last 2+years

but basically i just wanted to make sure nothing system necessary would be removed, worse case if something i run needs it-it would just prompt me to reinstall it right?

Right, or just run

```
sudo apt-get install -f
```

which will download any dependencies missing for installed packages.

---

