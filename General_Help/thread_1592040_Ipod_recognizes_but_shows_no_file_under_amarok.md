---
title: "Ipod recognizes but shows no file under amarok"
date: 2010-10-10
forum: General Help
---

### Post by gnulab on 2010-10-10
Hi,

I'm using KUbuntu 10.10 and I'm facing trouble playing music from my ipod touch 2G.

The system recognizes the ipod upon plugging in. Amarok 2.3.2 also recognizes the ipod, but it simply shows 0 tracks.

The instruction listed here [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
makes it look so easy.

I've tried 

```

df

```but ipod doesn't show up under any of the /dev/XXX. Is it suppose to enumerate as a /dev/XXX at all?

How do I proceed from here to troubleshoot this problem?

Thanks
Henry

---

### Post by Zorael on 2010-10-11
Known issue, the workaround is to download and install some packages from Lucid until fixed updates hit Maverick.

Related bug reports:
[list][*][bugs.kde.org #245648](https://bugs.kde.org/show_bug.cgi?id=245648): iphone zero tracks
[*][Launchpad #655908](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/655908): iphone zero tracks in amarok[/list]
> Please note :
1/ Reverting back to Lucid's packages libmtp8 & libmtp-dev
2/ Installing libimobiledevice0 from Lucid
just brings the ipod touch back in amarok with all its tracks !

Package downloads:
[list][*]**libimobiledevice0**
[i386](http://mirrors.kernel.org/ubuntu/pool/main/libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1_i386.deb) [amd64](http://mirrors.kernel.org/ubuntu/pool/main/libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1_amd64.deb)
[*]**libmtp8**
[i386](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_1.0.2-1ubuntu1_i386.deb) [amd64](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_1.0.2-1ubuntu1_amd64.deb)
[*]**libmtp-dev**
[i386](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp-dev_1.0.2-1ubuntu1_i386.deb) [amd64](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp-dev_1.0.2-1ubuntu1_amd64.deb)[/list]

The difficult thing is to keep the packages from upgrading to Maverick's versions. You can install them from the debs via the terminal or by double-clicking them in Dolphin, but then you would have to open your package manager (KPackageKit, QApt, Muon, Synaptic etc) and **hold** or **forbid-version** the package. Hold stops it from upgrading entirely, forbid-version makes it skip the version it wants to upgrade to but allows later upgrades (such as later versions when this has been fixed).

Package managers seldom respect eachother's hold settings. I exclusively use the terminal command-line **aptitude**, and putting these packages on forbid-version is very easy. But then KPackageKit still wants to upgrade them, so I have to go into its settings and disable automatic retrieval of available updates to get it to stop nagging (System Settings -> Software Updates -> Settings, Check for updates: Never). Also I disable the daemon entirely (System Settings -> Startup and Shutdown -> Service Manager, uncheck KPackageKit Service), since there's no point of it running when I only use the terminal anyway.

Example procedure follows. Ignore the prepended dollar signs; that's just convention to show they're (Debian non-root) terminal commands.
```
$ ARCH=**i386**                          # change i386 to **amd64** if you're running a 64-bit installation
$ cd /tmp
$ wget http://mirrors.kernel.org/ubuntu/pool/main/libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1_$ARCH.deb http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp8_1.0.2-1ubuntu1_$ARCH.deb http://mirrors.kernel.org/ubuntu/pool/main/libm/libmtp/libmtp-dev_1.0.2-1ubuntu1_$ARCH.deb
$ sudo dpkg -i libimobiledevice0*$ARCH.deb libmtp8*$ARCH.deb libmtp-dev*$ARCH.deb
$ sudo aptitude install libusb-dev   # missing dependency for some reason
$ sudo aptitude **forbid-version** libimobiledevice0 libmtp8 libmtp-dev   # ignore errors about packages not upgradable
```
Disconnect and reconnect your iPod, then try starting up Amarok again.

I'm not entirely sure those -dev packages are needed, but they're listed in the bug report, and I don't really have to worry about the minute drive space they need.

---

### Post by gnulab on 2010-10-11
man, you're c00l :D

I'll give it a go tonight!

---

### Post by jason.e.stewart on 2010-12-12
Yes!!! 

Thank you for such a complete answer. Worked great for me. The combination of google and ubuntu forums saved the day again.

:-)

---

### Post by mardukvmbc on 2010-12-21
No joy for me, ipod touch 8 gig. Any other ideas?

---

### Post by mardukvmbc on 2010-12-28
got it working, didn't have fuse installed...

---

### Post by livinjean on 2011-02-12
followed your guide, it worked like a charm.
thanks for the detailed information

---

