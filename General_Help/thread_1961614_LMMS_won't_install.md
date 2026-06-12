---
title: "LMMS won't install"
date: 2012-04-19
forum: General Help
---

### Post by 0011235813 on 2012-04-19
Hi,
I just tried to install a package called LMMS (Linux Multimedia Studio), I tried two ways; from the repositories in USC, and from an external repository via terminal. In both cases I was told that I had missing dependencies:

```
lmms : Depends: wine1.2 but it is not going to be installed
```
anyone know how to install this dependency?

---

### Post by haqking on 2012-04-19
then it needs wine.

```
sudo apt-get install wine
```

and you can get a more current LMMS from a PPA as detailed in thew LMMS site [http://lmms.sourceforge.net/wiki/index.php/Installation](http://lmms.sourceforge.net/wiki/index.php/Installation)

---

### Post by 0011235813 on 2012-04-19
> **haqking said:**
> then it needs wine.

```
sudo apt-get install wine
```

and you can get a more current LMMS from a PPA as detailed in thew LMMS site [http://lmms.sourceforge.net/wiki/index.php/Installation](http://lmms.sourceforge.net/wiki/index.php/Installation)

Trouble is, I **have** wine installed! I even tried opening the Windows version without success. But here is what USC tells me:
```
The following packages have unmet dependencies:

lmms: Depends: lmms-common (= 0.4.10-1ubuntu3) but 0.4.10-1ubuntu3 is to be installed
      Depends: lib32gcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
      Depends: lib32stdc++6 (>= 4.1.1) but 4.6.1-9ubuntu3 is to be installed
      Depends: libasound2 (> 1.0.24.1) but 1.0.24.1-0ubuntu10 is to be installed
      Depends: libc6 (>= 2.7) but 2.13-20ubuntu5.1 is to be installed
      Depends: libc6-i386 (>= 2.4) but 2.13-20ubuntu5.1 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
      Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
      Depends: libjack-0.116 but it is a virtual package
      Depends: libogg0 (>= 1.0rc3) but 1.2.2~dfsg-1ubuntu1 is to be installed
      Depends: libportaudio2 (>= 19+svn20101113) but 19+svn20110326-2 is to be installed
      Depends: libpulse0 (>= 0.9.23) but 1:1.0-0ubuntu3.1 is to be installed
      Depends: libqt4-xml (>= 4:4.5.3) but 4:4.7.4-0ubuntu8.1 is to be installed
      Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.4-0ubuntu8.1 is to be installed
      Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8.1 is to be installed
      Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu4 is to be installed
      Depends: libsndfile1 (>= 1.0.20) but 1.0.24-1ubuntu2 is to be installed
      Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is to be installed
      Depends: libvorbis0a (>= 1.1.2) but 1.3.2-1ubuntu2.1 is to be installed
      Depends: libvorbisenc2 (>= 1.1.2) but 1.3.2-1ubuntu2.1 is to be installed
      Depends: libvorbisfile3 (>= 1.1.2) but 1.3.2-1ubuntu2.1 is to be installed
      Depends: libxft2 (> 2.1.1) but 2.2.0-3ubuntu1 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

```

---

### Post by haqking on 2012-04-19
oh right, well im not familiar with LMMS myself i was just going by the message.

Hope you find a solution.

Peace

---

