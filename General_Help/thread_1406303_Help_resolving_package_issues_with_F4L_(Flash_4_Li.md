---
title: "Help resolving package issues with F4L (Flash 4 Linux)"
date: 2010-02-13
forum: General Help
---

### Post by Statik on 2010-02-13
Hi all,

I'm trying to get the program, F4L (Flash for Linux), which is a Flash EDITOR (not a player).

I tried MAKE'ng the source, found here: [http://sourceforge.net/projects/f4l/files/](http://sourceforge.net/projects/f4l/files/) and ran into errors.

So, I searched for a deb package and I found one here: [http://prdownloads.sourceforge.net/f4l/f4l_0.2-1_i386.deb?download](http://prdownloads.sourceforge.net/f4l/f4l_0.2-1_i386.deb?download)

However, installing it is problematic and I can't seem to resolve the dependences. It looks like the packages have been replaced with newer versions. The output is:

```
statik@statik-desktop:~/Desktop$ sudo dpkg -i --force-architecture f4l_0.2-1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 247346 files and directories currently installed.)
Preparing to replace f4l 0.2-1 (using f4l_0.2-1_i386.deb) ...
Unpacking replacement f4l ...
dpkg: dependency problems prevent configuration of f4l:
 f4l depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
 f4l depends on libqt3c102-mt (>= 3:3.3.4-3); however:
  Package libqt3c102-mt is not installed.
 f4l depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing f4l (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 f4l
statik@statik-desktop:~/Desktop$ 

```

I'm running Karmic AMD64.

Can anyone help?

Thanks

Statik

---

