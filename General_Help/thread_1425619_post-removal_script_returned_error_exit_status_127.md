---
title: "post-removal script returned error exit status 127"
date: 2010-03-09
forum: General Help
---

### Post by afrodeity on 2010-03-09
Eish, it's a hot day and nothing seems to be going right. Trying to figure a way out of this one - error 127. Looks like it could be Metacity problem? There a couple of pythons that also have a problem.



```
(Reading database ... 145089 files and directories currently installed.)
Preparing to replace metacity-common 1:2.28.0-0ubuntu1 (using .../metacity-common_1%3a2.28.0-0ubuntu2_all.deb) ...
Unpacking replacement metacity-common ...
/var/lib/dpkg/info/metacity-common.postrm: 11: update-gconf-defaults: not found
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 11: update-gconf-defaults: not found
dpkg: error processing /var/cache/apt/archives/metacity-common_1%3a2.28.0-0ubuntu2_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 11: update-gconf-defaults: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace python-libxml2 2.7.5.dfsg-1ubuntu1 (using .../python-libxml2_2.7.5.dfsg-1ubuntu1.1_i386.deb) ...
/var/lib/dpkg/info/python-libxml2.prerm: 6: update-python-modules: not found
dpkg: warning: old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: error processing /var/cache/apt/archives/python-libxml2_2.7.5.dfsg-1ubuntu1.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-libxml2.postinst: 6: update-python-modules: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace ubuntu-tweak 0.5.1-1~karmic1 (using .../ubuntu-tweak_0.5.2-1~karmic2_all.deb) ...
/var/lib/dpkg/info/ubuntu-tweak.prerm: 6: update-python-modules: not found
dpkg: warning: old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: error processing /var/cache/apt/archives/ubuntu-tweak_0.5.2-1~karmic2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/ubuntu-tweak.postinst: 6: update-python-modules: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace lernid 0.6~200~201003060503 (using .../lernid_0.6~203~201003090503_all.deb) ...
Unpacking replacement lernid ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/metacity-common_1%3a2.28.0-0ubuntu2_all.deb
 /var/cache/apt/archives/python-libxml2_2.7.5.dfsg-1ubuntu1.1_i386.deb
 /var/cache/apt/archives/ubuntu-tweak_0.5.2-1~karmic2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-yaml (3.09-1) ...
/var/lib/dpkg/info/python-yaml.postinst: 10: pycentral: not found
dpkg: error processing python-yaml (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-beagle (0.3.9-1) ...
/var/lib/dpkg/info/python-beagle.postinst: 6: update-python-modules: not found
dpkg: error processing python-beagle (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gtkspell (2.25.3-3ubuntu1) ...
/var/lib/dpkg/info/python-gtkspell.postinst: 6: update-python-modules: not found
dpkg: error processing python-gtkspell (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-eggtrayicon (2.25.3-3ubuntu1) ...
/var/lib/dpkg/info/python-eggtrayicon.postinst: 6: update-python-modules: not found
dpkg: error processing python-eggtrayicon (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on metacity-common (>= 1:2.28); however:
  Package metacity-common is not installed.
 metacity depends on metacity-common (<< 1:2.29); however:
  Package metacity-common is not installed.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
Setting up python-mediaprofiles (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-mediaprofiles.postinst: 6: update-python-modules: not found
dpkg: error processing python-mediaprofiles (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up sound-juicer (2.28.0-1) ...
/var/lib/dpkg/info/sound-juicer.postinst: 11: gconf-schemas: not found
dpkg: error processing sound-juicer (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: error processing ubuntu-tweak (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up python-evince (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-evince.postinst: 6: update-python-modules: not found
dpkg: error processing python-evince (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gtksourceview (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-gtksourceview.postinst: 6: update-python-modules: not found
dpkg: error processing python-gtksourceview (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gdl (2.25.3-3ubuntu1) ...
/var/lib/dpkg/info/python-gdl.postinst: 6: update-python-modules: not found
dpkg: error processing python-gdl (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gda (2.25.3-3ubuntu1) ...
/var/lib/dpkg/info/python-gda.postinst: 6: update-python-modules: not found
dpkg: error processing python-gda (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-totem-plparser (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-totem-plparser.postinst: 6: update-python-modules: not found
dpkg: error processing python-totem-plparser (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-evince (>= 2.28.0-0ubuntu1); however:
  Package python-evince is not configured yet.
 python-gnome2-desktop depends on python-gtksourceview (>= 2.28.0-0ubuntu1); however:
  Package python-gtksourceview is not configured yet.
 python-gnome2-desktop depends on python-mediaprofiles (>= 2.28.0-0ubuntu1); however:
  Package python-mediaprofiles is not configured yet.
 python-gnome2-desktop depends on python-totem-plparser (>= 2.28.0-0ubuntu1); however:
  Package python-totem-plparser is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up python-evolution (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-evolution.postinst: 6: update-python-modules: not found
dpkg: error processing python-evolution (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gtop (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-gtop.postinst: 6: update-python-modules: not found
dpkg: error processing python-gtop (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libmetacity0:
 libmetacity0 depends on metacity-common (>= 1:2.28); however:
  Package metacity-common is not installed.
 libmetacity0 depends on metacity-common (<< 1:2.29); however:
  Package metacity-common is not installed.
dpkg: error processing libmetacity0 (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnomeprint (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-gnomeprint.postinst: 6: update-python-modules: not found
dpkg: error processing python-gnomeprint (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
Setting up python-gksu2 (2.25.3-3ubuntu1) ...
/var/lib/dpkg/info/python-gksu2.postinst: 6: update-python-modules: not found
dpkg: error processing python-gksu2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-xlib (0.14-2) ...
Ignoring install-info called from maintainer script
The package python-xlib should be rebuild with new debhelper to get trigger support
/var/lib/dpkg/info/python-xlib.postinst: 11: update-python-modules: not found
dpkg: error processing python-xlib (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of rednotebook:
 rednotebook depends on python-yaml (>= 3.05); however:
  Package python-yaml is not configured yet.
dpkg: error processing rednotebook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-metacity:
 python-metacity depends on libmetacity0 (>= 1:2.25.8); however:
  Package libmetacity0 is not configured yet.
dpkg: error processing python-metacity (--configure):
 dependency problems - leaving unconfigured
Setting up python-chardet (1.0.1-1.1) ...
/var/lib/dpkg/info/python-chardet.postinst: 9: pycentral: not found
dpkg: error processing python-chardet (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: error processing python-libxml2 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up python-nautilusburn (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-nautilusburn.postinst: 6: update-python-modules: not found
dpkg: error processing python-nautilusburn (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-bugbuddy (2.28.0-0ubuntu1) ...
/var/lib/dpkg/info/python-bugbuddy.postinst: 6: update-python-modules: not found
dpkg: error processing python-bugbuddy (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up lernid (0.6~203~201003090503) ...
/var/lib/dpkg/info/lernid.postinst: 10: pycentral: not found
dpkg: error processing lernid (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up network-manager-gnome (0.8-0ubuntu3~nmt2~karmic) ...
/var/lib/dpkg/info/network-manager-gnome.postinst: 6: gconf-schemas: not found
dpkg: error processing network-manager-gnome (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on python-eggtrayicon (= 2.25.3-3ubuntu1); however:
  Package python-eggtrayicon is not configured yet.
 python-gnome2-extras depends on python-gtkspell (= 2.25.3-3ubuntu1); however:
  Package python-gtkspell is not configured yet.
 python-gnome2-extras depends on python-gksu2 (= 2.25.3-3ubuntu1); however:
  Package python-gksu2 is not configured yet.
 python-gnome2-extras depends on python-gdl (= 2.25.3-3ubuntu1); however:
  Package python-gdl is not configured yet.
 python-gnome2-extras depends on python-gda (= 2.25.3-3ubuntu1); however:
  Package python-gda is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of computertemp:
 computertemp depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing computertemp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-yaml
 python-beagle
 python-gtkspell
 python-eggtrayicon
 metacity
 python-mediaprofiles
 sound-juicer
 ubuntu-tweak
 python-evince
 python-gtksourceview
 python-gdl
 python-gda
 python-totem-plparser
 python-gnome2-desktop
 python-evolution
 python-gtop
 libmetacity0
 python-gnomeprint
 deskbar-applet
 python-gksu2
 python-xlib
 rednotebook
 python-metacity
 python-chardet
 python-libxml2
 python-nautilusburn
 python-bugbuddy
 lernid
 network-manager-gnome
 python-gnome2-extras
 computertemp
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

Current status: 16 updates [-1].
```

There is a tutorial about similar problem 
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

Not sure if I should remove entry for each single one in the database or not? This is the second time I've seen this happen, on a different machine, and one would think there is an automatic solution or utility to do this in Synaptic. Advice please.

---

### Post by afrodeity on 2010-03-09
```
Package: python-support
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 208
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 1.0.3ubuntu1
Depends: python (>= 2.5), dpkg (>= 1.14.19)
Conflicts: debhelper (<< 5.0.38)
Description: automated rebuilding support for Python modules
 This package contains the 'update-python-modules' script, which takes
 care of byte-compilation of Python-only modules.
 .
 Private modules are automatically rebuilt upon major Python upgrades,
 avoiding the need for strong dependencies.
 .
 Public modules are automatically made available for all installed
 Python versions.
Original-Maintainer: Josselin Mouette <joss@debian.org>

```

This could be the problem item?

---

### Post by afrodeity on 2010-03-10
metacity-common.postrm
```
#!/bin/sh
set -e
# Automatically added by dh_installcatalogs
if [ "$1" = "purge" ]; then
	rm -f /etc/sgml/metacity-common.cat /etc/sgml/metacity-common.cat.old
fi
# End automatically added section
# Automatically added by dh_gconf
if which update-gconf-defaults >/dev/null 2>&1; then
	update-gconf-defaults 
fi
# End automatically added section

```

python-libxml2.postinst
```
#!/bin/sh
#set -e
# Automatically added by dh_pysupport
if which update-python-modules >/dev/null 2>&1; then
	update-python-modules  python-libxml2.public
fi
# End automatically added section
```

---

### Post by afrodeity on 2010-03-10
Seems like the system is missing update-python-modules

---

### Post by afrodeity on 2010-03-10
```

sudo dpkg -i python-support_1.0.2ubuntu1_all.deb
(Reading database ... 144720 files and directories currently installed.)
Preparing to replace python-support 1.0.3ubuntu1 (using python-support_1.0.2ubuntu1_all.deb) ...
/var/lib/dpkg/info/python-support.prerm: 9: update-python-modules: not found
Unpacking replacement python-support ...
Setting up python-support (1.0.2ubuntu1) ...
/var/lib/dpkg/info/python-support.postinst: 20: update-python-modules: not found
dpkg: error processing python-support (--install):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for man-db ...
Errors were encountered while processing:
 python-support

```

---

### Post by afrodeity on 2010-03-14
I think this is my problem: update-gconf-defaults, should have spotted this right at the top, but stupidly went and googled the error code.

If I enter update-gconf-defaults in terminal I get this message:

```

bash: /usr/bin/update.gconf-defaults : /usr/bin/python: bad interpretter: no such file or directory

```

There are a number of posts on error 127 which suggest recreating the file.

In this case, all I need to do is make a symbolic link between /usr/bin/pyhon2.6 and /usr/bin/python since the problem is with interpretation which python setup to use, I have both 2.5 AND 2.6 installed!!!!

To make a symbolic link between /usr/bin/pyhon2.6 and /usr/bin/python

```

ln -s /usr/bin/python2.6 /usr/bin/python

```
 solved!!!

---

