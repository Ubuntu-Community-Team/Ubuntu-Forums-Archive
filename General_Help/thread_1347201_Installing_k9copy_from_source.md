---
title: "Installing k9copy from source"
date: 2009-12-05
forum: General Help
---

### Post by sarin_cv on 2009-12-05
I have downloaded the source package for k9copy 2.3.3. I don't know how to install this since I have tried only using ./configure and make. Please help

sarin@sarin-laptop:/media/Programs/Softwares/Linux/Ubuntu/Sources/k9copy-2.3.3-Source$ ls -l
total 74
drwxrwxrwx 1 root root     0 2009-12-06 08:57 cmake
-rwxrwxrwx 1 root root  9934 2009-08-20 12:35 CMakeLists.txt
-rwxrwxrwx 1 root root  1639 2009-08-20 12:35 config.h.cmake
-rwxrwxrwx 1 root root 18009 2009-08-20 12:35 COPYING
drwxrwxrwx 1 root root     0 2009-12-06 08:57 data
drwxrwxrwx 1 root root     0 2009-12-06 08:57 doc
-rwxrwxrwx 1 root root   884 2009-08-20 12:35 hi16-app-k9copy.png
-rwxrwxrwx 1 root root  2216 2009-08-20 12:35 hi32-app-k9copy.png
-rwxrwxrwx 1 root root  4001 2009-08-20 12:35 hi48-app-k9copy.png
drwxrwxrwx 1 root root  4096 2009-12-06 08:57 icons
-rwxrwxrwx 1 root root   465 2009-08-20 12:35 k9copy_assistant.desktop
-rwxrwxrwx 1 root root   460 2009-08-20 12:35 k9copy_assistant_open.desktop
-rwxrwxrwx 1 root root   443 2009-08-20 12:35 k9copy.desktop
-rwxrwxrwx 1 root root   413 2009-08-20 12:35 k9copy_open.desktop
-rwxrwxrwx 1 root root  1050 2009-08-20 12:35 k9copyui.rc
-rwxrwxrwx 1 root root  4047 2009-08-20 12:35 main.cpp
drwxrwxrwx 1 root root  4096 2009-12-06 08:57 po
-rwxrwxrwx 1 root root     0 2009-12-06 08:57 Project
-rwxrwxrwx 1 root root   794 2009-08-20 12:35 README
drwxrwxrwx 1 root root  4096 2009-12-06 08:57 src

---

### Post by sarin_cv on 2009-12-06
or does anybody have the deb for k9copy 2.3.3? coz 2.3.0 always crashes while opening a dvd...

---

### Post by Yellow Pasque on 2009-12-06
```
sudo apt-get build-dep k9copy
cmake
```

or: [https://launchpad.net/~mieszkoslusarczyk/+archive/kde4-extras-kde4.3](https://launchpad.net/~mieszkoslusarczyk/+archive/kde4-extras-kde4.3)

---

### Post by mc4man on 2009-12-06
You could try this to build your own .deb( just tested on karmic, worked fine, should be good for jaunty and intrepid also
Assuming you have build tools already but run this for build deps anyway

```
sudo apt-get install debhelper cmake kdelibs5-dev libxine-dev \
libdvdread-dev libqt4-opengl-dev libmpeg2-4-dev quilt \
dpkg-dev fakeroot libavcodec-dev libavformat-dev


```
then in order
```
mkdir k9build && cd k9build
```

```
wget http://www.debian-multimedia.org/pool/main/k/k9copy/k9copy_2.3.3-0.0.dsc

```

```
wget http://www.debian-multimedia.org/pool/main/k/k9copy/k9copy_2.3.3.orig.tar.gz
```

```
wget http://www.debian-multimedia.org/pool/main/k/k9copy/k9copy_2.3.3-0.0.diff.gz
```

```
dpkg-source -x *.dsc
```

```
cd k9copy-2.3.3
```

```
dpkg-buildpackage -rfakeroot -D -us -uc
```

As long as your libavcodec version is high enough you should be good to go, the .deb will be created in the k9build folder

( can't say how it will run, don't use k9

Edit:
if you're on hardy this won't work without updating your ffmpeg headers and debhelper ( debhelper update is in hardy-backports, for ffmpeg headers ask

Also note that those wgets are good as long as those source versions are avail. at debian-multimedia, files can be manually retrieved for future versions

edit: would not use this method (d-m .diff), and the latest (2.3.4) probably won't build on less than karmic
[here]("http://ubuntuforums.org/showthread.php?p=8698972#post8698972") for 2.3.4

---

### Post by sarin_cv on 2009-12-07
I'm using Jaunty... there are some issues with new libavcodec version in Jaunty ...so I reverted back to old version and decided to use dvd::rip ... I think it is better than k9..

---

