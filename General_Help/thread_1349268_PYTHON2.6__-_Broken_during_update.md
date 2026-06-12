---
title: "PYTHON2.6  - Broken during update"
date: 2009-12-08
forum: General Help
---

### Post by TBerk on 2009-12-08
I'm getting stuff like this:

```

$ sudo apt-get -f install python2.6-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python2.6-minimal
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
3 not fully installed or removed.
Need to get 0B/1,348kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 274590 files and directories currently installed.)
Preparing to replace python2.6-minimal 2.6.4-0ubuntu2 (using .../python2.6-minimal_2.6.4-0ubuntu3_i386.deb) ...
Moving /usr/lib/python2.6/site-packages/libtorrent.so to new location:
  --> /usr/lib/python2.6/old-site-packages/libtorrent.so (already exist in /usr/local/lib/python2.6/dist-packages/
mv: cannot move `/usr/lib/python2.6/site-packages/libtorrent.so' to `/usr/lib/python2.6/old-site-packages/': Not a directory
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Synaptic has trouble too:
```

E: /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb: subprocess new pre-installation script returned error exit status 1

```

What'll I do?

(Trying to uninstall/remove provides too many reliant apps that also would need to be removed. )

berk

---

