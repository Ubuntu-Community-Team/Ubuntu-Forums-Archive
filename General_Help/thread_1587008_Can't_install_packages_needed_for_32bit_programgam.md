---
title: "Can't install packages needed for 32bit program/game to run."
date: 2010-10-02
forum: General Help
---

### Post by TheOnlyMrK on 2010-10-02
I'm trying to get my game running but it gives me an error saying this;

```
You are running the Second Life Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/snowglobe-do-not-run-directly: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
```

So I figured okay that's simple enough, I'll just install the packages and it'll work, but it didn't.


```
michael@michael-laptop:~$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
Note, selecting ia32-libs instead of ia32-libs-gtk
ia32-libs is already the newest version.
E: Couldn't find package ia32-libs-kde
michael@michael-laptop:~$
```

I went to Synaptic Package Manager to see if I could find them manually but the only thing available is the ia32-libs and none of the other packages I need so I Googled the ones I couldn't find and downloaded the .deb packages for them from the Ubuntu website thinking it was just a problem with my sources.list because it looks like the packages are no longer used in Ubuntu but when I try to install them I get this;

```
(Reading database ... 133277 files and directories currently installed.)
Unpacking ia32-lib-gtk (from .../ia32-libs-gdk_16_amd64.deb) ...
dpkg: error processing /home/michael/Downoads/ia32-libs-gtk_16_amd64.deb (--install):
 trying to overwrite '/usr/lib32/at-spi/at-spi-registryd', which is also in package ia32-libs 0:2.7ubuntu 26
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors while processing:
 /home/michael/Downloads/ia32-libs-gtk_16_amd64.deb
```

So could anyone help please? I'm not a Linux noob anymore that's for sure but I'm still not too good at the under the hood work yet. The website for the program is this; [http://www.phoenixviewer.com/]("http://www.phoenixviewer.com/")

---

### Post by TheOnlyMrK on 2010-10-02
Figures after a couple hours of digging around Google I found out how to fix it, it's a problem with the program installing itself improperly on 64bit linux, the error it gave me just made it sound like a problem with Ubuntu. For anyone that may have this issue in the future download the three files at this website [http://jira.phoenixviewer.com/browse/PHOE-784](http://jira.phoenixviewer.com/browse/PHOE-784) and put them in the /lib folder and the program will start no problem.

---

