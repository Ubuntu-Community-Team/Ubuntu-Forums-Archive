---
title: "No package 'gconf-2.0' found"
date: 2009-10-29
forum: General Help
---

### Post by peterthegeek on 2009-10-29
I was trying to install GPointingDeviceSettings, started configuring it, and got this error:

```
checking for GTK+ - version >= 2.14.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for glib-genmarshal... no
checking for glib-mkenums... no
checking pkg-config is at least version 0.9.0... yes
checking for GCONF2... configure: error: Package requirements (gconf-2.0 >= 2.24.0) were not met:

No package 'gconf-2.0' found
```

But I'm pretty sure I have gconf-2.0 installed. Is it possible to have Gnome Configuration Editor installed and not have gconf-2.0 installed? To let you guys know I'm using Xfce, not sure that that matters.

---

### Post by LowSky on 2009-10-29
open synaptic and find out if its installed, or fomr the command line type

sudo apt-get install gconf

or 

sudo apt-get install gconf-2.0

or this command to find anything with that name 

find / -name gconf

---

### Post by Giblet5 on 2009-10-29
I never really looked, but this will tell you if you have it:

Open a terminal window and  ```
sudo dpkg -l | grep gconf
```

---

### Post by peterthegeek on 2009-10-29
Hmm, it looks like I already have it installed:

```
ii  compizconfig-backend-gconf                 0.8.2-0ubuntu2                            Settings library for plugins - OpenCompositing Project
ii  gconf-editor                               2.26.0-0ubuntu1                           An editor for the GConf configuration system
ii  gconf2                                     2.26.0-0ubuntu1                           GNOME configuration database system (support tools)
ii  gconf2-common                              2.26.0-0ubuntu1                           GNOME configuration database system (common files)
ii  libgconf2-4                                2.26.0-0ubuntu1                           GNOME configuration database system (shared libraries)
ii  libgconf2.24-cil                           2.24.0-3ubuntu1                           CLI binding for GConf 2.24
ii  pulseaudio-module-gconf                    1:0.9.14-0ubuntu20.2                      GConf module for PulseAudio sound server
ii  python-gconf                               2.26.1-0ubuntu1                           Python bindings for GConf2

```

---

### Post by mc4man on 2009-10-29
What it's looking for is this (or very similarly named

libgconf2-dev

Other things missing but maybe not needed ( use gnome here so don't know Xfce

libgtk2.0-dev

> checking for glib-genmarshal... no
checking for glib-mkenums... no


In libglib2.0-dev

---

### Post by peterthegeek on 2009-10-29
Ok thanks, I'll try installing libgconf2-dev once I'm finished upgrading to 9.10

---

### Post by Giblet5 on 2009-10-29
+1 on the libgconf2-dev

Anytime you're running a source package's autoconf (configure) script and it complains like that, search synaptic for the base package and install the xxx-dev package.

---

### Post by peterthegeek on 2009-10-30
What repo would have libgconf2-dev, and the other xxx-dev packages?

**EDIT:** Never mind! I forgot to refresh the packages after I changed the sources... and it worked! Thanks :D

**EDIT2:** Uhh, now it's saying "No package 'xi' found." :/

---

### Post by mc4man on 2009-10-30
>  Uhh, now it's saying "No package 'xi' found." :

As is quite typical stick a lib in front and search. If a -dev is found install, if just a lib install that.

In this case 
libxi-dev  (libxi6 is dependant lib ( on karmic

---

### Post by peterthegeek on 2009-10-30
That worked. It configured successfully! Now I'm getting this error when using the make command: "gpds-ui.c:364: error: &#8216;GpdsUIPriv&#8217; has no member named &#8216;gconf&#8217;"

---

