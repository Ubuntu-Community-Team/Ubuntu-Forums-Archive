---
title: "can't install libxvidcore4"
date: 2006-06-26
forum: General Help
---

### Post by glasyalabolis on 2006-06-26
hi, I am trying to install mplayer-586 and it depends on libxvidcore4. when apt tries to install libxvidcore4 I get this error, any help would be appreciated.

```
ron@the-glass-machine:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libxvidcore4
The following NEW packages will be installed:
  libxvidcore4
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
10 not fully installed or removed.
Need to get 0B/211kB of archives.
After unpacking 745kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115578 files and directories currently installed.)
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.1.0-final-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libxvidcore4_2%3a1.1.0-final-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libxvidcore.so.4.1', which is also in package xvidcore
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libxvidcore4_2%3a1.1.0-final-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

