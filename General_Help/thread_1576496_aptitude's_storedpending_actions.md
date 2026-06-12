---
title: "aptitude's stored/pending actions"
date: 2010-09-17
forum: General Help
---

### Post by ilna on 2010-09-17
In accordance with aptitude doc:

```
As a special case, “install” with no arguments will act on any stored/pending actions..."
```

OK, let's try:

```
~$ sudo aptitude -P -v install
The following NEW packages will be installed:
  libdirectfb-dev libdirectfb-extra libggi-target-vcsa{b} libgii1-target-x{b} libjpeg62-dev libprojectm-data libsysfs-dev 
  libxcb-render-util0-dev libxml-filter-buffertext-perl libxml-sax-writer-perl mplayer-skins plasma-widget-daisy 
  plasma-widget-fancytasks plasma-widget-xbar slv2-jack{b} 
The following packages will be REMOVED:
  gstreamer0.10-pulseaudio{u} hplip-cups{u} libestools1.2{u} libsane-hpaio{u} pulseaudio-utils{u} python-pexpect{u} rtkit{u} 
  sane-utils{u} yakuake{u} 
0 packages upgraded, 15 newly installed, 9 to remove and 1 not upgraded.
Need to get 1,560kB/2,760kB of archives. After unpacking 864kB will be used.
The following packages have unmet dependencies:
  slv2-jack: Depends: libslv2-9 (>= 0.6.4-1~) but it is not going to be installed.
  projectm-data: Conflicts: libprojectm-data (< 2.0.1) but 1.2.0-3 is to be installed.
  libgii1-target-x: Depends: libgii1 but it is not going to be installed.
  libggi-target-vcsa: Depends: libggi2 (>= 1:2.2.2) but it is not going to be installed.
                      Depends: libgii1 but it is not going to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libggi-target-vcsa [Not Installed]                 
2)     libgii1-target-x [Not Installed]                   
3)     libprojectm-data [Not Installed]                   
4)     slv2-jack [Not Installed]                          



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

Hm.. Something crazy.. What does it all mean? :)

---

### Post by andrewthomas on 2010-09-17
What are you trying to accomplish?

---

### Post by ilna on 2010-09-17
> **andrewthomas said:**
> What are you trying to accomplish?
I'd be happy to understand what does "stored/pending actions" mean, and, as a result, what does cited out mean.

---

