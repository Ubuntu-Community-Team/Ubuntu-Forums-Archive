---
title: "fail to add ppa repository"
date: 2012-04-13
forum: General Help
---

### Post by lsmgeb89 on 2012-04-13
I want to add GStreamer PPA repository, so I command
```
sudo add-apt-repository ppa:gstreamer-developers/ppa
```
But it always returns:
```
Error reading https://launchpad.net/api/1.0/~gstreamer-developers/+archive/ppa: Problem with the SSL CA cert (path? access rights?)
```
How to resolve it? Thanks!

---

### Post by daslinkard on 2012-04-14
What about trying the following sudo command:

```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly totem-plugins-extra
```

---

### Post by lsmgeb89 on 2012-04-14
> **daslinkard said:**
> What about trying the following sudo command:

```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly totem-plugins-extra
```
Hi daslinkard,
I have tried it: ```
sudo apt-get install libgstreamer0.10-0
```It seems works, but dirty with warning:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.0-freedesktop gir1.0-glib-2.0 gir1.0-gstreamer-0.10 libgirepository1.0-0 libgstreamer0.10-dev
Suggested packages:
  gstreamer0.10-doc
The following NEW packages will be installed:
  gir1.0-freedesktop gir1.0-glib-2.0 gir1.0-gstreamer-0.10 libgirepository1.0-0
The following packages will be upgraded:
  libgstreamer0.10-0 libgstreamer0.10-dev
2 upgraded, 4 newly installed, 0 to remove and 15 not upgraded.
Need to get 2,831kB of archives.
After this operation, 3,760kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libgstreamer0.10-dev libgstreamer0.10-0 gir1.0-gstreamer-0.10
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main gir1.0-freedesktop 0.6.8-1 [14.8kB]                 
Get:2 http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/ lucid/main libgstreamer0.10-dev 0.10.34-1~lucid1 [993kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main libgirepository1.0-0 0.6.8-1 [43.4kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/main gir1.0-glib-2.0 0.6.8-1 [116kB] 
Get:5 http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/ lucid/main libgstreamer0.10-0 0.10.34-1~lucid1 [1,600kB]                                    
Get:6 http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/ lucid/main gir1.0-gstreamer-0.10 0.10.34-1~lucid1 [63.4kB]                                  
Fetched 2,831kB in 19s (144kB/s)                                                                                                                            
Selecting previously deselected package gir1.0-freedesktop.
(Reading database ... 221348 files and directories currently installed.)
Unpacking gir1.0-freedesktop (from .../gir1.0-freedesktop_0.6.8-1_i386.deb) ...
Selecting previously deselected package libgirepository1.0-0.
Unpacking libgirepository1.0-0 (from .../libgirepository1.0-0_0.6.8-1_i386.deb) ...
Selecting previously deselected package gir1.0-glib-2.0.
Unpacking gir1.0-glib-2.0 (from .../gir1.0-glib-2.0_0.6.8-1_i386.deb) ...
Preparing to replace libgstreamer0.10-dev 0.10.28-1 (using .../libgstreamer0.10-dev_0.10.34-1~lucid1_i386.deb) ...
Unpacking replacement libgstreamer0.10-dev ...
Preparing to replace libgstreamer0.10-0 0.10.28-1 (using .../libgstreamer0.10-0_0.10.34-1~lucid1_i386.deb) ...
Unpacking replacement libgstreamer0.10-0 ...
Selecting previously deselected package gir1.0-gstreamer-0.10.
Unpacking gir1.0-gstreamer-0.10 (from .../gir1.0-gstreamer-0.10_0.10.34-1~lucid1_i386.deb) ...
Processing triggers for man-db ...
Setting up gir1.0-freedesktop (0.6.8-1) ...
Setting up libgirepository1.0-0 (0.6.8-1) ...

Setting up gir1.0-glib-2.0 (0.6.8-1) ...
Setting up libgstreamer0.10-0 (0.10.34-1~lucid1) ...

Setting up gir1.0-gstreamer-0.10 (0.10.34-1~lucid1) ...
Setting up libgstreamer0.10-dev (0.10.34-1~lucid1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```It will appreciated that you could indicate what causes this warning about the CA certification.Thanks a lot!

---

### Post by callmemahavir on 2012-04-14
What you are trying may be developer version...
Refer : 
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Please try the latest stable version of gstreamer.

---

### Post by lsmgeb89 on 2012-04-21
> **callmemahavir said:**
> What you are trying may be developer version...
Refer : 
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Please try the latest stable version of gstreamer.
I need gstreamer version >= 0.10.28, but the official repository's version is too low.
So I find the this ([http://delog.wordpress.com/2011/05/20/how-to-get-the-latest-version-of-gstreamer-on-ubuntu/](http://delog.wordpress.com/2011/05/20/how-to-get-the-latest-version-of-gstreamer-on-ubuntu/)).

---

