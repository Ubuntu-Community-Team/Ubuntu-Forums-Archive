---
title: "Valgrind installation problem"
date: 2010-10-21
forum: General Help
---

### Post by anup.techonly on 2010-10-21
Hi All,

I am trying to install valgrind, but it gives the following error:
```

anup@anup-desktop:~$ sudo apt-get install valgrind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pocketsphinx-hmm-wsj1 linux-headers-2.6.32-21-generic libpocketsphinx1 libtsmux0 libsphinxbase1 linux-headers-2.6.32-21 pocketsphinx-utils pocketsphinx-lm-wsj
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dbg
Suggested packages:
  kcachegrind alleyoop valkyrie
The following NEW packages will be installed:
  libc6-dbg valgrind
0 upgraded, 2 newly installed, 0 to remove and 143 not upgraded.
Need to get 58.6MB of archives.
After this operation, 175MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6-dbg 2.11.1-0ubuntu7.2
  404  Not Found

```valgrind is downloaded but libc6-dbg 2.11.1-0ubuntu7.2 can not be found in the repository. I checked h[http://in.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/](http://in.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/) here also.

Please help, I am stuck.

regards,
Anup

---

