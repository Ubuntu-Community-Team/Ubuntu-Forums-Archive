---
title: "Xubuntu 10.04 LTS Update Issue"
date: 2011-06-27
forum: General Help
---

### Post by fleamour on 2011-06-27
I am encountering this error when trying to install latest ubufox update from LP-PPA-mozillateam-firefoxstable of which the following details are provided:
```
E: /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb: trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0
```
  
```
(Reading database ... 311409 files and directories currently installed.)
Preparing to replace ubufox 0.9-0ubuntu1~mfs~lucid1 (using .../ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb) ...
Unpacking replacement ubufox ...
dpkg: error processing /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb (--unpack):
 trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0:0.9-0ubuntu1~mfs~lucid1
Errors were encountered while processing:
 /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
h
```

I was initially offered to report bug via Apport, but think I am out in cold due to non official ALSA configuration.  quite why this should matter I am unsure.  (Sound is very buggy on IBM T21 hardware & I have to recompile ALSA each new kernel) as per this guide:

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

:-(:-k:-(

EDIT: Synaptic legend shows ubufox as "Installed (upgradable)"

---

### Post by pqwoerituytrueiwoq on 2011-06-27
```
sudo apt-get remove xul-ext-ubufox
sudo apt-get install ubufox
```
problem solved have had the same issue on 64bit lucid ubuntu no issue on the 32bit oddly enough

---

### Post by fleamour on 2011-06-27
Thanks!

---

