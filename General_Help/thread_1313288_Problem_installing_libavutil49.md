---
title: "Problem installing libavutil49"
date: 2009-11-03
forum: General Help
---

### Post by linuxnovice on 2009-11-03
Hi,

Ok here is the reason why I want to install libavutil49:

I want to install robot-player-dev for my research work. However, it failed to install citing dependency issues. The dependency tree looks like this:

robot-player-dev -> libplayerdrivers2-dev -> libhighgui-dev -> libavcodec-dev -> libavutil-dev -> libavutil49.

Now, when I try to install libavutil49, here is what I get:

```
sudo apt-get install libavutil49
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad-multiverse
  libavcodec-unstripped-52 libavformat52 libavutil-unstripped-49
  libmjpegtools-1.9 libquicktime1
The following NEW packages will be installed:
  libavutil49
0 upgraded, 1 newly installed, 7 to remove and 0 not upgraded.
Need to get 89.7kB of archives.
After this operation, 13.9MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

I am not exactly sure, whether it will be a good idea to remove all those other packages. So, is there a work around for this? This only happens in 9.04.

Thanks.

---

### Post by mc4man on 2009-11-03
In 9.04 the -dev's of ffmpeg libraires cannot be installed with the unstripped libraries

So basically you're forced to replace the unstripped with the stripped libs and remove anything that depends on the unstripped versions when installing/using the -devs

After using the ffmpeg -devs, you can then remove them and re-install the unstripped libs and any other removed dependent packages.

(basically a pita

This has been addressed somewhat in karmic by allowing the ffmpeg 'extra'(unstripped) libs to be installed with the -devs 


Possible workarounds for jaunty would be to not install the package versions of the ffmpeg -devs and instead build ffmpeg with static libraries to /usr/local
This will provide the headers needed (what the -dev packages provide

The only problem there may be if you use a current/recent ffmpeg svn source, it may be unsuitable for robot-player-dev or in general due to the constant changes

here's a good guide to building, what you may wish to try is use the guide, don't build/install a new libx264, and checkout a slightly older ffmpeg source ( or even just use the same revision jaunty uses

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

jaunty ffmpeg source 
```
wget http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/ffmpeg-debian_0.svn20090303.orig.tar.gz

```

Or the slightly newer kamric source (may still work with the default libx264-65 that jaunty uses
```
wget http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/ffmpeg_0.5+svn20090706.orig.tar.gz
```

You could also post in that thread for further advice

---

### Post by linuxnovice on 2009-11-05
> **mc4man said:**
> In 9.04 the -dev's of ffmpeg libraires cannot be installed with the unstripped libraries

So basically you're forced to replace the unstripped with the stripped libs and remove anything that depends on the unstripped versions when installing/using the -devs

After using the ffmpeg -devs, you can then remove them and re-install the unstripped libs and any other removed dependent packages.

(basically a pita

This has been addressed somewhat in karmic by allowing the ffmpeg 'extra'(unstripped) libs to be installed with the -devs 


Possible workarounds for jaunty would be to not install the package versions of the ffmpeg -devs and instead build ffmpeg with static libraries to /usr/local
This will provide the headers needed (what the -dev packages provide

The only problem there may be if you use a current/recent ffmpeg svn source, it may be unsuitable for robot-player-dev or in general due to the constant changes

here's a good guide to building, what you may wish to try is use the guide, don't build/install a new libx264, and checkout a slightly older ffmpeg source ( or even just use the same revision jaunty uses

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

jaunty ffmpeg source 
```
wget http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg-debian/ffmpeg-debian_0.svn20090303.orig.tar.gz

```

Or the slightly newer kamric source (may still work with the default libx264-65 that jaunty uses
```
wget http://archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/ffmpeg_0.5+svn20090706.orig.tar.gz
```

You could also post in that thread for further advice

Hi,

Thank you for your help. However, I found the workaround too much work and I went ahead and installed libavutil49 anyway. I don't know what I've broken yet. Anyway, after this I tried to install robot-player-dev and it installed along with a bunch of other stuff.

Thanks,

---

