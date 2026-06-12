---
title: "Compiling Ubuntu packages in the Gentoo way?"
date: 2009-10-04
forum: General Help
---

### Post by dxxvi on 2009-10-04
I just tried to install Gentoo but it took so much time and I gave up. But Gentoo gave me some ideas. For example, we can [configure the compile options]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=5") (Ubuntu packages are for all kind of machines, so I'm afraid they were not compiled with all the flags for a little bit advanced machines) or we can use some flags to [make the system fully tweaked for Gnome]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6").

So my question is if there is anyway to specify those flags then download the source packages and compile them with those flags and if we can do that, will we see any performance improvement?

Thank you.

---

### Post by eric3_14159 on 2009-10-04
This might just be saying really obvious things you know, but if you run "apt-get source <package>" then you'll download a directory where you can run ./configure, make, and make install, or could edit the Makefile first, to get some of the tweaking you're talking about.

---

### Post by dxxvi on 2009-10-05
> **eric3_14159 said:**
> ... run ./configure, make, and make install, or could edit the Makefile first, to get some of the tweaking you're talking about.
Will I get a .deb file (for an easy application/package management and easy uninstallation) if I run configure, make and make install? I try to avoid configure, make and make install since I got a lot of pains with RedHat.
I found this [link]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/") and [this one from Ubuntu website]("https://help.ubuntu.com/community/CompilingSoftware") (quite old, not sure if it still holds for Karmic).

Thanks for your reply.

---

### Post by luctor on 2009-10-05
checkinstall will create deb packages from source.
I have run gentoo and ubuntu,I doubt if gentoo really makes that much difference in speed.

---

### Post by jocko on 2009-10-05
> **dxxvi said:**
> Will I get a .deb file (for an easy application/package management and easy uninstallation) if I run configure, make and make install? I try to avoid configure, make and make install since I got a lot of pains with RedHat.
I found this [link]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/") and [this one from Ubuntu website]("https://help.ubuntu.com/community/CompilingSoftware") (quite old, not sure if it still holds for Karmic).

Thanks for your reply.

> **luctor said:**
> checkinstall will create deb packages from source.
I have run gentoo and ubuntu,I doubt if gentoo really makes that much difference in speed.

Don't use checkinstall for that. The sources in the ubuntu repos already contain the proper instructions to build **real** debian packages (as opposed to the half functional packages you get from checkinstall).
First, to get what you need for compiling and producing debian packages:
```
sudo apt-get install build-essential fakeroot dpkg-dev
```Make sure you have "deb-src" activated in your sources.list (System-->Administration-->Software sources; check "source code" in the first tab).

To get what you need for building a specific package:
```
sudo apt-get build-dep [COLOR=Red]packagename[/COLOR]
```And to get the source in a subdirectory to the current directory (which preferably is somewhere in your home dir):
```
apt-get source packagename **##Note: Do [COLOR=Black]NOT[/COLOR] use sudo here.**
```To generate a debian package:
```
cd [COLOR=Red][path to the source code directory][/COLOR]
fakeroot debian/rules binary
```To change the compile options, I guess you should look in the scripts in the "debian" subdirectory in the source code directory.
To pass options to the build process, use something like this (text in red are what you normally would pass as options for the configure script):
```
DEB_BUILD_OPTIONS="[COLOR=Red]--prefix=/usr/local --enable-option1 --enable-option2 --disable-option3[/COLOR]" fakeroot debian/rules binary
```
(if you don't want the generated package to be replaced the next time it's updated in the repos, you need to change the version number in the last entry of the debian/changelog file in such a way that it always looks higher than the repo version.)


For an automated recompile of any package, there's also apt-build in the repos. It supposedly can re-build the entire system (apt-build world) from source with your optimisations. Not sure how well it works...

---

