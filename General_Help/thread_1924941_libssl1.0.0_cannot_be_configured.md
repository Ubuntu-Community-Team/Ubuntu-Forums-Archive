---
title: "libssl1.0.0 cannot be configured"
date: 2012-02-13
forum: General Help
---

### Post by exaflop on 2012-02-13
Each of my three machines running 11.10 have started doing this when I try to do any software installation or updates. For instance,

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libssl1.0.0 (--configure):
 libssl1.0.0:amd64 1.0.0e-2ubuntu4.2 cannot be configured because libssl1.0.0:i386 is in a different version (1.0.0e-2ubuntu4)
Errors were encountered while processing:
 libssl1.0.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot make any forward progress. Any advice? Many thanks.

---

### Post by exaflop on 2012-02-15
Here's how I fixed it:

```
sudo dpkg --purge --force-depends libssl1.0.0:i386
sudo dpkg --configure -a

```

---

### Post by imachavel on 2012-02-15
sudo dpkg --purge --force-depends libssl1.0.0:i386dpkg: libssl1.0.0: dependency problems, but removing anyway as you requested:
 libreoffice-core depends on libssl1.0.0 (>= 1.0.0).
 python-openssl depends on libssl1.0.0 (>= 1.0.0).
 openssh-client depends on libssl1.0.0 (>= 1.0.0).
 xchat depends on libssl1.0.0 (>= 1.0.0).
 apache2.2-bin depends on libssl1.0.0 (>= 1.0.0).
 iputils-ping depends on libssl1.0.0 (>= 1.0.0).
 encfs depends on libssl1.0.0 (>= 1.0.0).
 libssl-dev depends on libssl1.0.0 (= 1.0.0e-2ubuntu4.2).
 libnet-ssleay-perl depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0 is to be removed.
 libssh-4 depends on libssl1.0.0 (>= 1.0.0).
 rdesktop depends on libssl1.0.0 (>= 1.0.0).
 apache2-utils depends on libssl1.0.0 (>= 1.0.0).
 libsasl2-modules depends on libssl1.0.0 (>= 1.0.0).
 telepathy-idle depends on libssl1.0.0 (>= 1.0.0).
 libcurl3 depends on libssl1.0.0 (>= 1.0.0).
 libubuntuone-1.0-1 depends on libssl1.0.0 (>= 1.0.0).
 transmission-gtk depends on libssl1.0.0 (>= 1.0.0).
 wget depends on libssl1.0.0 (>= 1.0.0).
 tcpdump depends on libssl1.0.0 (>= 1.0.0).
 python2.7-minimal depends on libssl1.0.0 (>= 1.0.0).
 libsnmp15 depends on libssl1.0.0 (>= 1.0.0).
 gstreamer0.10-plugins-bad depends on libssl1.0.0 (>= 1.0.0).
 virtuoso-opensource-6.1-bin depends on libssl1.0.0 (>= 1.0.0).
 virtuoso-opensource-6.1-common depends on libssl1.0.0 (>= 1.0.0).
 libcrypt-ssleay-perl depends on libssl1.0.0 (>= 1.0.0).
 libdns69 depends on libssl1.0.0 (>= 1.0.0).
 libvirtodbc0 depends on libssl1.0.0 (>= 1.0.0).
 virtualbox depends on libssl1.0.0 (>= 1.0.0).
 isc-dhcp-server-ldap depends on libssl1.0.0 (>= 1.0.0).
 openssl depends on libssl1.0.0 (>= 1.0.0).
 libpython2.7 depends on libssl1.0.0 (>= 1.0.0).
 wpasupplicant depends on libssl1.0.0 (>= 1.0.0).
(Reading database ... 308869 files and directories currently installed.)
Removing libssl1.0.0 ...
Purging configuration files for libssl1.0.0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
danel@danel-Dimension-4700:~$ sudo dpkg --configure -a


no kidding? I hope it helps me in the feature, auto remove removes all unused packages from repository correct? It's funny you posted a fix, because someone else just made a thread with the exact same issue

---

### Post by jhuebner on 2012-08-28
WOW that worked for me too... Thank you!

---

