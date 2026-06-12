---
title: "Ubuntu maverick meerkat 10.10 xrdp troubles"
date: 2010-10-24
forum: General Help
---

### Post by haihovu on 2010-10-24
I am having some problems in the xrdp area which affect one of my Ubuntu servers since upgrading from 10.04 to 10.10. The problem is currently not observed on a laptop with a fresh install of 10.10, i.e. not upgraded from earlier version. The problems appear to be multi-facet and gradually escalating. Below is a chronicle describing this.

- The host is an old Dell desktop with a 1.6GHz P4.
- Have beein running Ubuntu on it since 7.X, and been upgrading for every normal release since then.
- Standard install with most desktop as well as a few server options.
- Running samba file service, print service, DNS service.
- Have xrdp set up to run with tightvnc for ages and this worked more or less satisfactorily for a long time.
- When upgraded to maverick two weeks ago xrdp appeared to work fine, that is until a slew of updates sometimes last week was picked up, after which RDP clients showed up with a terminal on a thatched background without any other desktop component when connected to this server.
- A few more updates were picked up Friday which appeared to include libc among other things, after which xrdp started to crash with the below error everytime a client connected to it:
Oct 22 18:06:32 server kernel: [36242.868081] xrdp[7902]: segfault at 0 ip 0026c7f1 sp b767ec18 error 4 in libc-2.12.1.so[1f8000+157000]
- Then I messed around with downloading xrdp source from [http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/) and built and installed it on the Ubuntu server which didn't seem to even want to start, so I removed all artifacts created as a result of the installation procedure.
- Now Synaptic can't properly install xrdp, I tried to uninstall and reinstall xrdp several times via Synaptic, which gave indication that everything completed successfully except that there were only a few files installed under /usr/share/xrdp, the rest (/etc/xrdp, /etc/init.d, /etc/pam.d, ...) are missing!
- The log showed absolutely nothing when installing/uninstalling xrdp via Synaptic. I know Synaptic still works because I can still install/uninstall other packages, just not xrdp.

So it seems something is really screwed up in my distro now, can someone give me some tips as to how to get to the bottom of this?

---

### Post by haihovu on 2010-10-24
Installing xrdp via apt-get looks innocent enough, though still yield the same result, some parts of the installed files are missing:

sudo apt-get install xrdp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xrdp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/251kB of archives.
After this operation, 1,696kB of additional disk space will be used.
Selecting previously deselected package xrdp.
(Reading database ... 170986 files and directories currently installed.)
Unpacking xrdp (from .../xrdp_0.5.0~20100303cvs-4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up xrdp (0.5.0~20100303cvs-4) ...

Synaptic showed these are being installed with xrdp:

/.
/etc
/etc/default
/etc/default/xrdp
/etc/init.d
/etc/init.d/xrdp
/etc/pam.d
/etc/pam.d/sesman
/etc/pam.d/xrdp-sesman
/etc/xrdp
/etc/xrdp/km-0407.ini
/etc/xrdp/km-0409.ini
/etc/xrdp/km-040c.ini
/etc/xrdp/km-0410.ini
/etc/xrdp/km-0419.ini
/etc/xrdp/km-041d.ini
/etc/xrdp/sesman.ini
/etc/xrdp/startwm.sh
/etc/xrdp/xrdp.ini
/usr
/usr/bin
/usr/bin/xrdp-genkeymap
/usr/bin/xrdp-keygen
/usr/bin/xrdp-sesadmin
/usr/bin/xrdp-sesrun
/usr/lib
/usr/lib/xrdp
/usr/lib/xrdp/libcommon.so
/usr/lib/xrdp/libcommon.so.0
/usr/lib/xrdp/libcommon.so.0.0.0
/usr/lib/xrdp/libmc.so
/usr/lib/xrdp/libmc.so.0
/usr/lib/xrdp/libmc.so.0.0.0
/usr/lib/xrdp/librdp.so
/usr/lib/xrdp/librdp.so.0
/usr/lib/xrdp/librdp.so.0.0.0
/usr/lib/xrdp/libscp.so
/usr/lib/xrdp/libscp.so.0
/usr/lib/xrdp/libscp.so.0.0.0
/usr/lib/xrdp/libvnc.so
/usr/lib/xrdp/libvnc.so.0
/usr/lib/xrdp/libvnc.so.0.0.0
/usr/lib/xrdp/libxrdp.so
/usr/lib/xrdp/libxrdp.so.0
/usr/lib/xrdp/libxrdp.so.0.0.0
/usr/lib/xrdp/libxup.so
/usr/lib/xrdp/libxup.so.0
/usr/lib/xrdp/libxup.so.0.0.0
/usr/sbin
/usr/sbin/xrdp
/usr/sbin/xrdp-chansrv
/usr/sbin/xrdp-sesman
/usr/sbin/xrdp-sessvc
/usr/share
/usr/share/doc
/usr/share/doc/xrdp
/usr/share/doc/xrdp/changelog.Debian.gz
/usr/share/doc/xrdp/copyright
/usr/share/doc/xrdp/rsakeys.ini
/usr/share/man
/usr/share/man/man5
/usr/share/man/man5/sesman.ini.5.gz
/usr/share/man/man5/xrdp.ini.5.gz
/usr/share/man/man8
/usr/share/man/man8/xrdp-keygen.8.gz
/usr/share/man/man8/xrdp-sesman.8.gz
/usr/share/man/man8/xrdp-sesrun.8.gz
/usr/share/man/man8/xrdp.8.gz
/usr/share/xrdp
/usr/share/xrdp/ad24b.bmp
/usr/share/xrdp/ad256.bmp
/usr/share/xrdp/cursor0.cur
/usr/share/xrdp/cursor1.cur
/usr/share/xrdp/sans-10.fv1
/usr/share/xrdp/xrdp24b.bmp
/usr/share/xrdp/xrdp256.bmp

It appears that almost everything are there except for any of the artifacts slated to be placed under /etc. Though while the installation was in progress I can see that these files appeared temporarily under /etc/xrdp but disappeared when the installation completed, leaving an empty directory:

km-0407.ini.dpkg-new
km-0410.ini.dpkg-new
sesman.ini.dpkg-new
km-0409.ini.dpkg-new 
km-0419.ini.dpkg-new
startwm.sh.dpkg-new
km-040c.ini.dpkg-new
km-041d.ini.dpkg-new
xrdp.ini.dpkg-new

---

### Post by haihovu on 2010-10-24
OK, there was probably some configuration artifacts left behind somehow in my previous installs, because when I did a complete removal as opposed to just removal, xrdp is now purring like a kitten with a ball of yarn.

---

