---
title: "how can i download lucid-updates/allpackages at once(in zip/tar foramt)"
date: 2011-04-04
forum: General Help
---

### Post by connect2jan on 2011-04-04
hi
i am installing vlc offline(i dont have internet connection) on ubuntu 10.04 (lucid)
the following site is very good to all packages

[http://packages.ubuntu.com/lucid-upates/allpackages](http://packages.ubuntu.com/lucid-upates/allpackages)

when i installing vlc .deb file
aniket@aniket:~/Downloads$ sudo dpkg -i vlc_1.1.4-1ubuntu1.4_i386.deb 
sudo: unable to resolve host aniket
(Reading database ... 123831 files and directories currently installed.)
Preparing to replace vlc 1.1.4-1ubuntu1.4 (using vlc_1.1.4-1ubuntu1.4_i386.deb) ...
Unpacking replacement vlc ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.4-1ubuntu1.4); however:
  Package vlc-nox is not configured yet.
 vlc depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is not installed.
  Package libavcodec-extra-52 is not installed.
 vlc depends on libavutil50 (>= 4:0.6-1~) | libavutil-extra-50 (>= 4:0.6-1~); however:
  Package libavutil50 is not installed.
  Package libavutil-extra-50 is not installed.
 vlc depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4 is not installed.
 vlc depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not installed.
 vlc depends on libsdl-image1.2 (>= 1.2.10); however:
  Package libsdl-image1.2 is not installed.
 vlc depends on libtar; however:
  Package libtar is not installed.
 vlc depends on libva-x11-1; however:
  Package libva-x11-1 is not installed.
 vlc depends on libva1; however:
i went cafe i downloaded some of few, among above,and tried
still again its showing some pkg missing
so 
>how can i/where can i get  download all lucid-updates at once(in zip/tar) instead of  downloading each single package
>can i copy from ubuntu live cd,will it work
thanku

---

### Post by zvacet on 2011-04-05
You are trying to install maverick packages in lucid.I don´t know how smart that is.If you want you can try [Keryx]("http://keryxproject.org/") fif you don't have internet at home.

---

