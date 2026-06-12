---
title: "Package dependencies cannot be resolved"
date: 2012-05-14
forum: General Help
---

### Post by Thelinuxgeek on 2012-05-14
I tried downloading media player codecs and got this error: Package dependencies cannot be resolved


The following packages have unmet dependencies:

gstreamer0.10-ffmpeg: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                      Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1 is to be installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                      Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                      Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
gstreamer0.10-ffmpeg:i386: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed


I tried sudo apt-get -f install to fix any broken packages but it didn't work, this was returned:

isaac@Flappy:~$ sudo apt-get -f install
[sudo] password for isaac: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libgomp1:i386 libcroco3:i386 libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by matt_symes on 2012-05-15
Hi

That looks like dependency hell there :)

Can we take a look at your sources.

Open a terminal and type

```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Copy and past the output from that command between code tags like this

[noparse]```
 output 
```[/noparse]

to get output like this

```
 output 
```

Kind regards

---

### Post by Thelinuxgeek on 2012-05-15
Sorry, output code is a little confusing, but here's the output:


/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-icons-precise.list:deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-icons-precise.list:deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-icons-precise.list.save:deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-icons-precise.list.save:deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-swar-themes-precise.list:deb [http://ppa.launchpad.net/noobslab/swar-themes/ubuntu](http://ppa.launchpad.net/noobslab/swar-themes/ubuntu) precise main
/etc/apt/sources.list.d/noobslab-swar-themes-precise.list:deb-src [http://ppa.launchpad.net/noobslab/swar-themes/ubuntu](http://ppa.launchpad.net/noobslab/swar-themes/ubuntu) precise main

---

### Post by matt_symes on 2012-05-15
Hi

I expected to see an unholy mix of ppa's and repo versions :) That's what usually causing these problems.

However, it seems to be a known problem.

Take a look at this thread.

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/971012](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/971012)

Poster #9 had a solution that worked for a couple of people.

Kind regards

---

### Post by hariskhalique on 2012-08-30
I try almost every thing that I know by cleaning my cache and what found related to this but i found this helped

You need to install unmet dependencies etc gstreamer0.10-ffmpeg to install this first you need to install libavcodec53 libavcodec-extra-53 libavformat53 to install this libavcodec53, libgsm1 libschroedinger-1.0-0, libavcodec53, libavcodec-extra-53 libavformat53, gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, ffmpeg or you can try like this

sudo apt-get install libgsm1 libschroedinger-1.0-0 libavcodec53 libavcodec-extra-53 libavformat53 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad ffmpeg

if it says to install any unmet dependencies then install them first.

or you can wait for ubuntu developer but I dont know who told them to focused on GUI

I hope it will help you

---

### Post by SlugSlug on 2012-08-30
try aptitude instead of apt-get 

I think you need to ```
apt-get install aptitude 
``` on 12.04+

then you would type 

```
sudo aptitude install ....
```

---

