---
title: "kdenlive dependency confilicts"
date: 2009-08-23
forum: General Help
---

### Post by nicedanmonkey on 2009-08-23
I'm trying to install the latest version of Kdenlive and have gotten into trouble with dependencies.  It wants to uninstall vlc, blender, winff and a bunch of other stuff. I believe it has something to do with a new newer mlt library it's downloading. Without going through and uninstalling everything is there a way to install Kdenlive? Is it possible to keep the Kdenlive dependencies separate so they don't conflict with everything else? 

I am using the subab PPA which is what the kdenlive website recommends.
[https://launchpad.net/~sunab/+archive/ppa](https://launchpad.net/~sunab/+archive/ppa)
And I've also tried the unstable PPA
[https://launchpad.net/~sunab/+archive/sunab2](https://launchpad.net/~sunab/+archive/sunab2)

---

### Post by paul.gevers on 2009-08-24
> **nicedanmonkey said:**
> Without going through and uninstalling everything is there a way to install Kdenlive?

Really depends on the dependencies. It would help if you showed the output of you package manager, and tell us which package manager you are using. You might be able to tell it exactly what it needs to do, ie you then solve the dependency chain yourself.

> **nicedanmonkey said:**
>  Is it possible to keep the Kdenlive dependencies separate so they don't conflict with everything else? 


Not that I know of. But you might be able to set appropriate priorities.

---

### Post by brunolabs on 2009-08-24
Does Kdenlive work without problems under GNOME?

---

### Post by Cuba71 on 2009-08-25
My installation of Kenlive on Jaunty 9.04  freezes at the config windows.
I have no clue why.

---

### Post by nicedanmonkey on 2009-08-25
> **paul.gevers said:**
> Really depends on the dependencies. It would help if you showed the output of you package manager, and tell us which package manager you are using. You might be able to tell it exactly what it needs to do, ie you then solve the dependency chain yourself.

Here is what my package manager tells me. I'm using the Synaptic Package Manager.

> kdenlive:
 Depends: libmlt++2 but it is not going to be installed
 Depends: libmlt1 but it is not going to be installed
 Depends: melt but it is not going to be installed
 Depends: libavdevice-unstripped-52 but it is not going to be installed
 Depends: libavfilter-unstripped-0 but it is not going to be installed
 Depends: libswscale-unstripped-0 but it is not going to be installed
 Depends: libpostproc-unstripped-51 but it is not going to be installed


If I try to install libmlt1...

> libmlt1:
 Depends: libavcodec-unstripped-52 but it is not going to be installed or
 	libavcodec-unstripped--unstripped-52 (>=3:0.svn20090303-1) but it is not installable
 Depends: libavformat-unstripped-52 but it is not going to be installed or
 	libavformat-unstripped--unstripped-52 (>=3:0.svn20090303-1) but it is not installable
 Depends: libswscale-unstripped-0 but it is not going to be installed or
 	libswscale-unstripped--unstripped-0 (>=3:0.svn20090303-1) but it is not installable
 Depends: libavcodec-unstripped-52 but it is not going to be installed
 Depends: libavformat-unstripped-52 but it is not going to be installed
 Depends: libswscale-unstripped-0 but it is not going to be installed

I could probably go to each of those dependencies and follow the trail, uninstalling the dependencies that are ultimately causing the problem but I'd rather not do that. But, I suppose that if Ubuntu doesn't have a way of installing dependencies separately, or keeping them contained just within Kdenlive I don't really have a choice.

---

### Post by nicedanmonkey on 2009-08-25
> **brunolabs said:**
> Does Kdenlive work without problems under GNOME?

Kdenlive has worked fairly well for me in the past under GNOME. It's not always the easiest program to get up and running but it's been pretty stable. They've been getting better and better with each new release.

---

### Post by paul.gevers on 2009-08-26
> **nicedanmonkey said:**
> libmlt1:
Depends: libavcodec-unstripped-52 but it is not going to be installed or libavcodec-unstripped--unstripped-52 (>=3:0.svn20090303-1) but it is not installable
Depends: libavformat-unstripped-52 but it is not going to be installed or libavformat-unstripped--unstripped-52 (>=3:0.svn20090303-1) but it is not installable
Depends: libswscale-unstripped-0 but it is not going to be installed or libswscale-unstripped--unstripped-0 (>=3:0.svn20090303-1) but it is not installable

This really doesn't look good (see the double unstripped--unstripped, these do not exist). I think there is a problem in the specifications of libmlt1. What is it's source? You should file a bug report for that.

Maybe if you try first to install libavdevice-unstripped-52, libavfilter-unstripped-0, libswscale-unstripped-0, and libpostproc-unstripped-51 manually (shouldn't be any problem, if it is than please report). Hopefully then you will be able to procede.

---

### Post by nicedanmonkey on 2009-09-08
I found a way to get Kdenlive to install. I used a different repository this time.
[https://launchpad.net/~intuitivenipple/+archive/video-editors](https://launchpad.net/~intuitivenipple/+archive/video-editors)

Which I found at the Kdenlive forums
[http://www.kdenlive.org/forum/development-snapshot-ubuntu-packages](http://www.kdenlive.org/forum/development-snapshot-ubuntu-packages)

The only thing is when you install Kdenlive it breaks VNC and totem. Here is the fix that I got from the Kdenlive forums.

> An update to address the issue of the new libavutil shared-object version having bumped to 50 (from 49).

The effect of this is that applications that depend on libavutil49 or libavutil-unstripped-49 (such as totem via gstreamer-ffmpeg or vlc and vlc-nox) will be unable to process formats managed by the ffmpeg libraries.

There is a simple fix, which is to add a symbolic link from the -49 library name to the -50 library:


sudo ln -s /usr/lib/libavutil.so.50.3.0 /usr/lib/libavutil.so.49

---

