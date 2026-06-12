---
title: "Need to fix package system..."
date: 2010-11-12
forum: General Help
---

### Post by Quadunit404 on 2010-11-12
Okay, I JUST got back on my laptop now that I have my new A/C adapter, and guess what? The package management system is broken! Which sucks, because I have quite a bit of updates to install.

Here's the details provided by Synaptic when installing the new version of AWN:

```
E: /var/cache/apt/archives/libawn1-trunk_0.4.1~bzr778+201011111458~maverick1_amd64.deb: short read on buffer copy for backend dpkg-deb during `./usr/lib/libawn.so.1.0.1'
E: /var/cache/apt/archives/avant-window-navigator-trunk_0.4.1~bzr778+201011111458~maverick1_amd64.deb: short read on buffer copy for backend dpkg-deb during `./usr/lib/awn/applets/simple-launcher/simple-launcher.so'
E: /var/cache/apt/archives/avant-window-navigator-data-trunk_0.4.1~bzr778+201011111458~maverick1_all.deb: short read on buffer copy for backend dpkg-deb during `./usr/share/icons/hicolor/48x48/apps/avant-window-navigator.png'
E: /var/cache/apt/archives/awn-applets-common-trunk_0.4.1~bzr1476+201011032003~maverick1_amd64.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/awn-applets-c-core-trunk_0.4.1~bzr1476+201011032003~maverick1_amd64.deb: short read on buffer copy for backend dpkg-deb during `./usr/lib/awn/applets/awnsystemmonitor/awnsystemmonitor.so'
E: /var/cache/apt/archives/awn-applets-c-extras-trunk_0.4.1~bzr1476+201011032003~maverick1_amd64.deb: short read on buffer copy for backend dpkg-deb during `./usr/lib/awn/applets/webapplet/webapplet.so'
E: /var/cache/apt/archives/python-awn-extras-trunk_0.4.1~bzr1476+201011032003~maverick1_amd64.deb: short read on buffer copy for backend dpkg-deb during `./usr/share/pyshared/awn/extras/awnlib.py'
E: /var/cache/apt/archives/awn-applets-python-core-trunk_0.4.1~bzr1476+201011032003~maverick1_all.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/awn-applets-python-extras-trunk_0.4.1~bzr1476+201011032003~maverick1_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/awn-settings-trunk_0.4.1~bzr778+201011111458~maverick1_all.deb: short read on buffer copy for backend dpkg-deb during `./usr/bin/awn-settings'


```

---

### Post by Hippytaff on 2010-11-12
How are you trying to install the updates
does
```

sudo apt-get update && sudo apt-get upgrade

```
work?

---

### Post by Quadunit404 on 2010-11-12
Using the Update Manager, as usual.

And nope, that didn't work either. Here's the terminal output:

```
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
(Reading database ... 180356 files and directories currently installed.)
Preparing to replace libxml2-utils 2.7.7.dfsg-4 (using .../libxml2-utils_2.7.7.dfsg-4ubuntu0.1_amd64.deb) ...
Unpacking replacement libxml2-utils ...
dpkg: error processing /var/cache/apt/archives/libxml2-utils_2.7.7.dfsg-4ubuntu0.1_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mysql-common 5.1.49-1ubuntu8 (using .../mysql-common_5.1.49-1ubuntu8.1_all.deb) ...
Unpacking replacement mysql-common ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/mysql-common_5.1.49-1ubuntu8.1_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/mysql-common/internal-use-only/_etc_mysql_debian-start'
Preparing to replace python-libxml2 2.7.7.dfsg-4 (using .../python-libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb) ...
Unpacking replacement python-libxml2 ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/python-libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/pyshared/python2.6/libxml2mod.so'
No apport report written because MaxReports is reached already
                                                              dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/xserver-xorg-video-intel_2%3a2.12.0-1ubuntu5.1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb
 /var/cache/apt/archives/libxml2-utils_2.7.7.dfsg-4ubuntu0.1_amd64.deb
 /var/cache/apt/archives/mysql-common_5.1.49-1ubuntu8.1_all.deb
 /var/cache/apt/archives/python-libxml2_2.7.7.dfsg-4ubuntu0.1_amd64.deb
 /var/cache/apt/archives/xserver-xorg-video-intel_2%3a2.12.0-1ubuntu5.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Hippytaff on 2010-11-12
Right...to be honest...I don't know whats happening here...though someone more proficient than  me in the way of the ubuntu will...in the mean time I'll do some googling :-)

---

### Post by Quadunit404 on 2010-11-12
Fixed it :D

Turns out one of the programs I installed was screwing with APT so I uninstalled it and now APT works right again.

---

### Post by Hippytaff on 2010-11-12
Excellent :-D

Remember to mark the thread as solved in the thread tools at the top of the page so that if others encounter the same problem they'll know that you fixed it :-D

---

