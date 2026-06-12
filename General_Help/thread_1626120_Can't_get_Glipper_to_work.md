---
title: "Can't get Glipper to work"
date: 2010-11-19
forum: General Help
---

### Post by jacatone on 2010-11-19
I'm running Ubuntu 10.04. I downloaded and installed glipper, but don't seem to be able to launch it. Anyone know a solution? Thanks.

---

### Post by rotave on 2010-11-20
Glipper was been abandoned back in 2007; it was very buggy. I would download Glippy and install that instead; it does the same thing and is current. There is a ppa for it here: [https://launchpad.net/~bikooo/+archive/glippy]("https://launchpad.net/~bikooo/+archive/glippy")

---

### Post by jacatone on 2010-11-21
Can't seem to install Glippy. How do you install a PPA in Ubuntu 10.04. Seems I'm supposed to do that first. When I try compiling the glippy tarball I get the following error message:

root@compaq:/home/jacatone/Desktop/Downloads/glippy-0.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gmcs... /usr/bin/gmcs
checking pkg-config is at least version 0.9.0... yes
checking for GTK_SHARP_20... yes
checking for GCONF_SHARP_20... no
configure: error: Package requirements (gconf-sharp-2.0) were not met:

No package 'gconf-sharp-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GCONF_SHARP_20_CFLAGS
and GCONF_SHARP_20_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I was able to install the gconf-sharp-2.10.4 tarball so I don't understand why it can't find it.

---

### Post by robert shearer on 2010-11-21
> **jacatone said:**
> I'm running Ubuntu 10.04. I downloaded and installed glipper, but don't seem to be able to launch it. Anyone know a solution? Thanks.

right click on a panel and select 'add to panel'.
Scroll down to clipboard manager and  select and add.

Then just start it from the panel applet that is added to your panel.


> Glipper was been abandoned back in 2007; it was very buggy. 

Glipper has always worked perfectly here.
 Currently running it trouble-free in instances of 8.04, 10.04 and 10.10.

---

