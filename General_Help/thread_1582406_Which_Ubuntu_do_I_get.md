---
title: "Which Ubuntu do I get?"
date: 2010-09-26
forum: General Help
---

### Post by viperwontbyte on 2010-09-26
Hi everybody. I need to install ubuntu on a Vista Pc. I have skimmed over a little bit on the topic of Linux and have chosen ubuntu. I have a project to that requires I have linux on my pc. I'm going to write a C++ program that targets that platform. I came very close to downloading ubuntu desktop edion but cancelled the download after about 30 seconds because I'm not sure if this is what I need. Maybe I need ubuntu server? I need the following as a pre-requisite of the project: cvs, autoconf >= 2.57a, automake >= 1.8, libtool >= 1.4.2, gettext >= 0.12.1, make >= 3.79, tar, bunzip2 (bzip2), gunzip (gzip), path, infocmp (ncurses-bin / ncurses-devel), gcc 2.95 or >= 3.0, g++ 2.95 or >= 3.0, flex, bison, pkg-config, wget, libpng2 or libpng3 (DirectFB), zlib (development headers). So will i have all this stuff if I download the desktop edition of ubuntu? And if the answer is "yes"; do I have to manually install the above items after the initial install? I intentions are to download ubuntu, then burn the download to a CD. Then install from the CD. I need help with this. Please.

---

### Post by cottfcfan on 2010-09-26
Desktop Edition should be fine.
I've checked most of the packages you list.
Some appear to be installed by default the rest are all in "synaptic package Manager".
Probably no more than a 5 minute job to install everything you need.

---

### Post by unknownPoster on 2010-09-26
Desktop edition will be fine. To get most, if not all of the software you listed, you can run the following command in a terminal:

```

sudo apt-get install build-essential

```

---

### Post by psycho5 on 2010-09-26
First install build-essential 

then if still something is missing, you can manually install them from synaptic package manager. You can also install build-essential from synaptic as well.

---

