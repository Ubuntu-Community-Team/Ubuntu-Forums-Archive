---
title: "more up to date software in synaptic?"
date: 2009-09-13
forum: General Help
---

### Post by zerobotman on 2009-09-13
admittedly i'm a noob to ubuntu but i can't stand to use windows for anything but windows games (and they're slowly getting too boring for me to keep the partition). one thing i find though is that the software i download with synaptic seems to be out of date much of the time and i'd really like to know if i can make it download from more up to date locations. is there better 3rd party software perhaps?

---

### Post by pythonscript on 2009-09-13
It depends on what software you're talking about. A major part of ubuntu is its staggered release cycle, where major upgrades to software (like Firefox 3.5, for example) are only included in each new major release that comes out every 6 months. If you're interested in a linux distribution with that always gives you the most up to date software, I suggest you check out something like Arch Linux.

---

### Post by zerobotman on 2009-09-13
> **pythonscript said:**
> It depends on what software you're talking about. A major part of ubuntu is its staggered release cycle, where major upgrades to software (like Firefox 3.5, for example) are only included in each new major release that comes out every 6 months. If you're interested in a linux distribution with that always gives you the most up to date software, I suggest you check out something like Arch Linux.

hmm i'll give that a try. what is it based off?

---

### Post by kerry_s on 2009-09-13
> **zerobotman said:**
> hmm i'll give that a try. what is it based off?

arch is it's own distro & not based off any other distro. it is not really meant for a beginner. the kind of setup your looking for is called a rolling release, not many do that any more for stability reasons.
[http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

normally, i would recommend debian testing, but the last time i tried it was messed up.

---

### Post by jerrrys on 2009-09-13
launchpad is a good source

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

and i like this one

[http://appnr.com/](http://appnr.com/)

---

### Post by pythonscript on 2009-09-13
Arch may not be for beginners, but you certainly learn a good deal as you configure it,  and Ubuntu can't come *close* to it in terms of speed or the final size of the installation.

---

### Post by lswb on 2009-09-13
OS Software developers these days usually have a web site where you can find the latest versions for download. If they have a .deb package it is usually relatively easy to install with the benefit that it is tracked by the usual apt/dpkg/synaptic tools. Even some closed-source programs are available as debs.

The other common package format is .rpm package which is used by Red Hat/Fedora and some other distributions. There is a program called "alien" which will convert (with varying degree of success) .rpm to .deb

Often though all that is available is a "tarball" ( .tar.gz or tar.bz2 file) that needs manual installation. There is no standard method for installing these. Some contain binaries/executables but probably most are source files that must be compiled and installed after downloading. Usually a README or INSTALL file is included in the tarball that explains how to install, or instructions are on the developer's website. There many forum threads and howtos that go into details of installing from source if you decide to try.

---

### Post by jmszr on 2009-09-13
zerobotman.

This is a good source: [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by pythonscript on 2009-09-13
+1 on getdeb.net. I've used that for songbird and tucan (some of the only apps I use that aren't in the repos).

---

### Post by XCan on 2009-09-14
> **lswb said:**
> OS Software developers these days usually have a web site where you can find the latest versions for download. If they have a .deb package it is usually relatively easy to install with the benefit that it is tracked by the usual apt/dpkg/synaptic tools. Even some closed-source programs are available as debs.

The other common package format is .rpm package which is used by Red Hat/Fedora and some other distributions. There is a program called "alien" which will convert (with varying degree of success) .rpm to .deb

Often though all that is available is a "tarball" ( .tar.gz or tar.bz2 file) that needs manual installation. There is no standard method for installing these. Some contain binaries/executables but probably most are source files that must be compiled and installed after downloading. Usually a README or INSTALL file is included in the tarball that explains how to install, or instructions are on the developer's website. There many forum threads and howtos that go into details of installing from source if you decide to try.

Also, I've found many devs providing their own repos, so your app can update itself automatically as they release new version. Wine is an example of this.

---

### Post by steveneddy on 2009-09-14
> **jerrrys said:**
> launchpad is a good source

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

and i like this one

[http://appnr.com/](http://appnr.com/)

this is bad advice - 

to the OP - go to the developer's or the home page of the software that you need newer versions of and just install the ppa and have the dependencies taken care of at the same time as the software installation.

Blindly installing software for the sake of being able to do it is bad advice.

A newer version of Ubuntu or a  distro like Arch or gentoo with rolling updates may be more your style.

The versions of software offered for a particular distro are kept due to the various software dependencies throughout the installed version.

I have a few ppa's installed for software that I needed to run properly for my needs but only after referring to the web site and having the dev offer a ppa for my Ubuntu version.

---

