---
title: "What to add in /etc/apt/sources.list ?"
date: 2010-03-24
forum: General Help
---

### Post by mutombo1 on 2010-03-24
Someone has edited the sources.list file and now apt-get just doesn't work. When i try to do apt-get update, it gives me errors:

```
Get:1 http://deb.opera.com stable Release.gpg [189B]                           
Ign http://deb.opera.com stable/non-free Translation-mk             
Hit http://deb.opera.com stable Release                     
Ign http://deb.opera.com stable/non-free Packages           
Hit http://deb.opera.com stable/non-free Packages
Ign http://archive.ubuntu.com feisty Release.gpg     
Ign http://archive.ubuntu.com feisty/universe Translation-mk
Ign http://archive.ubuntu.com feisty Release
Ign http://archive.ubuntu.com feisty/universe Packages
Ign http://archive.ubuntu.com feisty/universe Sources
Err http://archive.ubuntu.com feisty/universe Packages                         
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com feisty/universe Sources                          
  404 Not Found [IP: 91.189.88.46 80]
Fetched 1B in 12s (0B/s)                                                       
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

My /etc/apt/sources.list looks like the following:

```

# deb cdrom:[Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)]/ feisty main multiverse restricted universe

#deb cdrom:[Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)]/ feisty main multiverse restricted universe

#deb http://mk.archive.ubuntu.com/ubuntu/ feisty main multiverse restricted universe
#deb http://mk.archive.ubuntu.com/ubuntu/ feisty-updates main multiverse restricted universe
#deb http://mk.archive.ubuntu.com/ubuntu/ feisty-security main multiverse restricted universe

#deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse

#deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

#deb http://http.us.debian.org/debian stable main contrib non-free
#deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
#deb http://security.debian.org stable/updates main contrib non-free

deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe
```

My lsb_release -a is:

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
```


Pleae help me, i can't install ANYTHING on my computer! Tell me what exactly to do in the sources.list and i wil lbe very thankful!

---

### Post by spiderbatdad on 2010-03-24
I would think because feisty is no longer supported. I do not see feisty listed at [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)
Perhaps time to upgrade.

---

### Post by mutombo1 on 2010-03-24
Okay but how to upgrade ?

And how can i install mplayer/vlc by using some other method ?

---

### Post by spiderbatdad on 2010-03-24
You can try to build vlc and mplayer from source. Just search vlc source and get result like: [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)
It may or may not build on your system...of course you would have to have build-essential installed before trying to compile source code.

Upgrading is the only thing that makes sense. Lucid Lynx (long term support) is available in beta now...it will be final release end of next month. So upgrading to that now will involve a lot of file updating over the next month...requiring fast internet connection.
[http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)
Or install Karmic the current release...which will expire in a year or so.

---

### Post by mutombo1 on 2010-03-24
Well build-essential is not installed because it is not possible by apt-get...

Please help me i don't know what to do and i need vlc/mplayer NOW!

---

### Post by spiderbatdad on 2010-03-24
> Well build-essential is not installed because it is not possible by apt-get...

Please help me i don't know what to do and i need vlc/mplayer NOW!

It is possible mplayer is on your installation cd...not sure. I doubt vlc is. You can try installing vlc for ubuntu from here:
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Search for mplayer also. If all else fails try uncommenting the cd-rom selection at the top of your sources.list, by removing the # symbol. Then run synaptic package manager and search for mplyer. If none of that works, you may have to stomp your feet and scream.

---

### Post by mutombo1 on 2010-03-24
Ok i try to upgrade feisty but there's another problem now:

```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 38, in <module>
    import apt
  File "/usr/lib/python2.5/site-packages/apt/__init__.py", line 2, in <module>
    import apt_pkg
ImportError: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
```

This is what i get when i type update-manager (in order to update the feisty to newer versions). Can someone help me pls ?

---

### Post by oldos2er on 2010-03-24
I don't think upgrading is possible, since you have to step through each version released since 7.04, and 7.10's support has also reached its end-of-life.

Btw, you can try changing your sources.list repositories to "old-releases": [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

---

### Post by Sef on 2010-03-24
> I don't think upgrading is possible, since you have to step through each  version released since 7.04, and 7.10's support has also reached its  end-of-life.

That is correct.  I would do a clean install.  I would wait - if you can - and install Lucid Lynx.

---

