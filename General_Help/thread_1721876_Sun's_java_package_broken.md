---
title: "Sun's java package broken"
date: 2011-04-05
forum: General Help
---

### Post by ilyail3 on 2011-04-05
I can't seem to install sun-java6-bin from the partner repository
```

Get:1 http://archive.canonical.com/ubuntu/ maverick/partner sun-java6-bin i386 6.24-1build0.10.10.1 [30.0MB]
Fetched 30.0MB in 23s (1,293kB/s)                                                                                    
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-bin_6.24-1build0.10.10.1_i386.deb  Hash Sum mismatch

```
I also tried to download the file manually, and install it(using dpkg -i) and got:
```

dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid stored block lengths'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing sun-java6-bin_6.24-1build0.10.10.1_i386.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/rt.jar'
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 sun-java6-bin_6.24-1build0.10.10.1_i386.deb

```
who should I report it to? I found the partner forum, however I can't post it there(get permission denied)

---

### Post by ajgreeny on 2011-04-05
Try removing the errant sun-java6-bin package from /var/cache/apt/archives either manually or with the command ```
sudo apt-get clean
```which removes everything, and try installing java again.  You may have a corrupt package in the cache at the moment which keeps trying to install without success.

---

