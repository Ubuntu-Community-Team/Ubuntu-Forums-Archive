---
title: "Broken Packages"
date: 2010-11-18
forum: General Help
---

### Post by NoNameWill on 2010-11-18
I have 9 broken packages that won't reinstall in synaptic or by terminal. This what I get from apt-get -f install 

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcrypto++8 linux-headers-2.6.32-21-generic iw linux-headers-2.6.32-21
  libfltk1.1 libupnp3 dkms libmpeg3-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 libmagickcore2
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libmagickcore2
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
4 not fully installed or removed.
Need to get 0B/6,115kB of archives.
After this operation, 6,144kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 760 package 'libmagickcore2':
 `Depends' field, invalid package name `libfreetype6!': character `!' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

