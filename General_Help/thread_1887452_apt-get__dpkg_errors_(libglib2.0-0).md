---
title: "apt-get / dpkg errors (libglib2.0-0)"
date: 2011-11-27
forum: General Help
---

### Post by shoot2kill on 2011-11-27
Hi, I am having a problem with updating my Oneiric installation.

I am trying to do a simple 'sudo apt-get update && sudo apt-get upgrade' and I get the following error:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gir1.2-glib-2.0 : Depends: libglib2.0-0 (>= 2.31.2) but 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0) but 2.31.3+git20111124.fcc69fd3-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.31.3+git20111124.fcc69fd3-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.31.3+git20111124.fcc69fd3-0ubuntu1~11.10~ricotz0) but 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0 is installed
E: Unmet dependencies. Try using -f.

```

'sudo apt-get install -f' produces this error:
```

(Reading database ... 248059 files and directories currently installed.)
Preparing to replace libglib2.0-0 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-0_2.31.3+git20111124.fcc69fd3-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Unpacking replacement libglib2.0-0 ...
dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.31.3+git20111124.fcc69fd3-0ubuntu1~11.10~ricotz0_amd64.deb (--unpack):
 './usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-0_2.31.3+git20111124.fcc69fd3-0ubuntu1~11.10~ricotz0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and, finally 'sudo dpkg --configure -a' gives the following error:
```

Errors were encountered while processing:
 libglib2.0-bin
 gir1.2-glib-2.0
 gir1.2-gtk-3.0
 gir1.2-vte-2.90
 gnome-shell
 libglib2.0-0:i386
 eog
 gir1.2-atspi-2.0
 gir1.2-gnomedesktop-3.0
 software-center
 libpango1.0-0:i386
 gir1.2-clutter-1.0
 gir1.2-pango-1.0
 gnome-tweak-tool
 ubuntu-desktop
 gir1.2-mutter-3.0
 gir1.2-freedesktop

```

ANY help would be greatly appreciated. Thanks

---

### Post by jerrrys on 2011-11-28
Got anything weird going on in your software sources?

Also you may want to consider doing away with the 
ricotz ppa

---

### Post by ventrical on 2011-11-28
Also try to open synaptic package manager, click <edit> and choose <fix broken packages>.

---

### Post by shoot2kill on 2011-12-05
Thanks. Removing the ricotz PPA seemed to work.

:)

---

