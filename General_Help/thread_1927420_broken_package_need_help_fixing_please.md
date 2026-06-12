---
title: "broken package need help fixing please"
date: 2012-02-18
forum: General Help
---

### Post by petermg on 2012-02-18
Here is what is happening:


```
petermg@kids-ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcinelerra-xt ttf-symbol-replacement pmount
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libguicast1 libmpeg3cine libquicktimecine
The following NEW packages will be installed:
  libguicast1 libmpeg3cine libquicktimecine
0 upgraded, 3 newly installed, 0 to remove and 245 not upgraded.
1 not fully installed or removed.
Need to get 0B/3,050kB of archives.
After this operation, 8,606kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 304746 files and directories currently installed.)
Unpacking libguicast1 (from .../libguicast1_1%3a2.2-0.3~ppa1~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libguicast1_1%3a2.2-0.3~ppa1~lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libguicast.so.1.0.0', which is also in package libcinelerra-xt 0:2.1.1-git20100325~ppa5~lucid
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libmpeg3cine (from .../libmpeg3cine_1%3a2.2-0.3~ppa1~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpeg3cine_1%3a2.2-0.3~ppa1~lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libavutil-cinelerra.so.49.6.0', which is also in package libcinelerra-xt 0:2.1.1-git20100325~ppa5~lucid
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libquicktimecine (from .../libquicktimecine_1%3a2.2-0.3~ppa1~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libquicktimecine_1%3a2.2-0.3~ppa1~lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libquicktimehv-1.6.0.so.1.0.0', which is also in package libcinelerra-xt 0:2.1.1-git20100325~ppa5~lucid
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libguicast1_1%3a2.2-0.3~ppa1~lucid1_i386.deb
 /var/cache/apt/archives/libmpeg3cine_1%3a2.2-0.3~ppa1~lucid1_i386.deb
 /var/cache/apt/archives/libquicktimecine_1%3a2.2-0.3~ppa1~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Rubi1200 on 2012-02-18
Hi,

try the following commands and report errors as before:

```
sudo apt-get clean
sudo apt-get install -f
sudo dpkg --configure -a
```

Might be useful to also post the output of this:

```
cat /etc/apt/sources.list
```

---

