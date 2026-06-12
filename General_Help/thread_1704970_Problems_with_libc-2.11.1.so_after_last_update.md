---
title: "Problems with libc-2.11.1.so after last update"
date: 2011-03-11
forum: General Help
---

### Post by isutoshi on 2011-03-11
Hi,

I updated my 10.04 system today from Ubuntu repos and now I find XBMC media center crashing as soon as I start a video.

/var/log/messages (dmesg has the same) output:
```
kernel: [4771050.644430] xbmc.bin[2156]: segfault at a02b000 ip b60ead3e sp bff71a4c error 4 in libc-2.11.1.so[b5fda000+153000]
```

Any ideas would be greatly appreciated!

Edit:
Here is the apt log:
```
Log started: 2011-03-11  17:47:04
[...]
Preparing to replace xbmc 2:10.00~svn35648-lucid1 (using .../xbmc_2%3a10.1~ppa1~lucid_all.deb) ...
Unpacking replacement xbmc ...
Preparing to replace xbmc-skin-confluence 2:10.00~svn35648-lucid1 (using .../xbmc-skin-confluence_2%3a10.1~ppa1~lucid_all.deb) ...
Unpacking replacement xbmc-skin-confluence ...
Preparing to replace xbmc-data 2:10.00~svn35648-lucid1 (using .../xbmc-data_2%3a10.1~ppa1~lucid_all.deb) ...
Unpacking replacement xbmc-data ...
Preparing to replace xbmc-bin 2:10.00~svn35648-lucid1 (using .../xbmc-bin_2%3a10.1~ppa1~lucid_i386.deb) ...
Unpacking replacement xbmc-bin ...
[...]
Setting up xbmc-bin (2:10.1~ppa1~lucid) ...
Setting up xbmc-data (2:10.1~ppa1~lucid) ...

Setting up xbmc-skin-confluence (2:10.1~ppa1~lucid) ...
Setting up xbmc (2:10.1~ppa1~lucid) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Log ended: 2011-03-11  17:47:40

```
Seems like XBMC is the culprit... but how do I rollback?

---

### Post by oldmilwaukee on 2012-03-06
This fixed it for me. 

rm -rf /var/cache/apt/*.bin

---

