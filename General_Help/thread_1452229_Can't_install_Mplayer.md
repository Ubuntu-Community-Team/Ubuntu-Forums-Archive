---
title: "Can't install Mplayer"
date: 2010-04-11
forum: General Help
---

### Post by maghoxfr on 2010-04-11
I'm trying to play/rip a movie and can't nor with Thoggen, Dvd::rip or Acidrip. I can't even play it with VLC. I installed the libdvdcss2 but nothing. When I try to install mp&#314;ayer I end up with 2 broken packages because it conflicts with my graphics card nvidia.

Ideas?

---

### Post by bobcollard on 2010-04-11
> **maghoxfr said:**
> I'm trying to play/rip a movie and can't nor with Thoggen, Dvd::rip or Acidrip. I can't even play it with VLC. I installed the libdvdcss2 but nothing. When I try to install mp&#314;ayer I end up with 2 broken packages because it conflicts with my graphics card nvidia.

Ideas?
Try this URL, it worked for me.  Read it carefully and follow the instructions.  Know that this is for more than one kind of system, so, only use what you need, like ubuntu, not kubuntu etc.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by maghoxfr on 2010-04-11
Thanks, great link, I'm still having problems installing mplayer, i get this:

 > mplayer: Depends: libvdpau1 but will not be installed or
                    libvdpau but will not be installed
  mplayer-nogui: Depends: libvdpau1 but will not be installed or
                          libvdpau but will not be installed


---

### Post by bobcollard on 2010-04-11
> **maghoxfr said:**
> Thanks, great link, I'm still having problems installing mplayer, i get this:
Try opening Synaptic Package Manager and search for these dependents.  It may be you don't have the repositories checked so you aren't getting the right version.  You can check that in Synaptic too under Settings.  Search on Google too for the exact version required.

---

### Post by WinterRain on 2010-04-11
Go to system>administration>software sources and make all repos are checked off, including the partner repos in the "other software" tab. Then reload.

---

### Post by maghoxfr on 2010-04-11
I''m still getting this message when trying to get mplayer from synaptic

```
E: /var/cache/apt/archives/libvdpau1_0.4-2~karmic~nvidiavdpauppa4_i386.deb: trying to overwrite «/usr/lib/libvdpau.so.1», which is also in the package nvidia-195-libvdpau 0
```

---

### Post by WinterRain on 2010-04-11
Try:
```
sudo apt-get clean && sudo apt-get autoremove
```
to clear your cache. Then try again.

---

### Post by maghoxfr on 2010-04-11
> The following packages wil be REMOVED:
  exiv2 kde-icons-oxygen kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 libclucene0ldbl libexiv2-5 libknotificationitem1
  liblzma0 libplasma3 libqt4-dbus libqt4-designer libqt4-opengl libqt4-phonon
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-webkit libsoprano4 libstreamanalyzer0
  libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0 nvidia-195-modaliases
  qjackctl soprano-daemon


Isn't this going to create a problem?

---

### Post by bobcollard on 2010-04-11
> **maghoxfr said:**
> I''m still getting this message when trying to get mplayer from synaptic

```
E: /var/cache/apt/archives/libvdpau1_0.4-2~karmic~nvidiavdpauppa4_i386.deb: trying to overwrite «/usr/lib/libvdpau.so.1», which is also in the package nvidia-195-libvdpau 0
```
I don't understand this, the newer version should take precedent.  Hope someone else can help.

---

### Post by no2498 on 2010-04-11
odd thinking smplayer is the 1 we need now it comes with the 264 code for mp4

type it in a terminal it tells you how to install it

hope this helps

---

### Post by wilee-nilee on 2010-04-11
> **no2498 said:**
> odd thinking smplayer is the 1 we need now it comes with the 264 code for mp4

type it in a terminal it tells you how to install it

hope this helps

Yes smplayer a better choice and is actually attached to Mplayer, vlc is very good as well.

---

### Post by lidex on 2010-04-11
Did you add the repository for the vdpau-mplayer? If you want vdpau, I would suggest adding this repository:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic")
Uninstall Mplayer and update to the versions there as they are designed to work together.

---

### Post by maghoxfr on 2010-04-11
Thanks for all the answers but I'm still getting some error notifications no matter what, i must be doing something wrong for sure.

---

