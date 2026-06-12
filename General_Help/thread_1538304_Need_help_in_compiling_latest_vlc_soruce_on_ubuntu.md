---
title: "Need help in compiling latest vlc soruce on ubuntu 10.04"
date: 2010-07-24
forum: General Help
---

### Post by mjsilverstri on 2010-07-24
Hi,

I am trying to run './configure' for vlc on ubuntu 10.04. I am getting this error:

```
checking for AVCODEC... no
configure: error: Could not find libavcodec or libavutil. Use --disable-avcodec to ignore this error.
```
But I already install libavcodec-div, but it still fails:

```
$ sudo apt-get install libavcodec-devReading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
I have checked '/usr/lib', I see the libavcodec.so:

-rw-r--r-- 1 root root 7339558 2010-03-04 04:42 libavcodec.a
lrwxrwxrwx 1 root root      21 2010-06-26 00:38 libavcodec.so -> libavcodec.so.52.20.1
lrwxrwxrwx 1 root root      21 2010-05-10 22:30 libavcodec.so.52 -> libavcodec.so.52.20.1
-rw-r--r-- 1 root root 5560152 2010-03-04 04:54 libavcodec.so.52.20.1
-rw-r--r-- 1 root root 1316312 2010-03-04 04:42 libavformat.a
lrwxrwxrwx 1 root root      22 2010-06-26 00:38 libavformat.so -> libavformat.so.52.31.0
lrwxrwxrwx 1 root root      22 2010-05-10 22:30 libavformat.so.52 -> libavformat.so.52.31.0
-rw-r--r-- 1 root root  694880 2010-03-04 04:42 libavformat.so.52.31.0
-rw-r--r-- 1 root root   85164 2010-03-04 04:42 libavutil.a
lrwxrwxrwx 1 root root      20 2010-06-26 00:38 libavutil.so -> libavutil.so.49.15.0
lrwxrwxrwx 1 root root      20 2010-05-10 22:30 libavutil.so.49 -> libavutil.so.49.15.0
-rw-r--r-- 1 root root   47296 2010-03-04 04:54 libavutil.so.49.15.0
```

---

