---
title: "ia32-libs broken"
date: 2011-02-16
forum: General Help
---

### Post by p3tris on 2011-02-16
Hi, during the latest update I got this:

```
Selecting previously deselected package lib32ncursesw5.
(Reading database ... 348379 files and directories currently installed.)
Unpacking lib32ncursesw5 (from .../lib32ncursesw5_5.7+20100626-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/lib32ncursesw5_5.7+20100626-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/lib32/libncursesw.so.5.7', which is also in package ia32-libs 20090808ubuntu10~wineppa3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace ia32-libs 20090808ubuntu10~wineppa3 (using .../ia32-libs_20090808ubuntu10~wineppa4_amd64.deb) ...
Unpacking replacement ia32-libs ...
Preparing to replace libssl0.9.8 0.9.8o-1ubuntu4.3 (using .../libssl0.9.8_0.9.8o-1ubuntu4.4_amd64.deb) ...
Unpacking replacement libssl0.9.8 ...
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/lib32ncursesw5_5.7+20100626-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libssl0.9.8 (0.9.8o-1ubuntu4.4) ...
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on lib32ncursesw5; however:
  Package lib32ncursesw5 is not installed.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ia32-libs

```

Now I get "ia32-libs package is broken". Any ideas how to proceed?

Thanks!

Update:
solved by reinstalling lib32ncursesw5 package. don't know why it failed to begin with!

---

### Post by Me Mechant on 2011-02-16
Thanks for the info, i got the same problem with the update this morning. Reinstall lib32ncursesw5 remove the error and now everything is fine!

---

### Post by flying sheep on 2011-02-16
thanks, this fixed it for me, too!

---

