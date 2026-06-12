---
title: "Problem Installing/uninstalling apps"
date: 2010-06-09
forum: General Help
---

### Post by Vadhil on 2010-06-09
I just recently upgraded to Ubuntu 10.04 and for some reason I cant seem to install or remove apps. Im consistently getting this error message:

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 10080 package 'xorg':
 `Provides' field, invalid package name `'x-window-system': must start with an alphanumeric

Cant find any help online so I figured I'd come here. Im a linux noob and any help would be appreciated.

Thanks.

---

### Post by arrange on 2010-06-09
Can you post the **/var/lib/dpkg/available** file somewhere? (not here, it's going to be long, but you could compress it)

?Can you also post the output of```

ls -l /var/lib/dpkg/available*

```

---

### Post by Vadhil on 2010-06-09
Output:

ls -l /var/lib/dpkg/available*
-rw-r--r-- 1 root root 2359676 2010-05-26 12:59 /var/lib/dpkg/available
-rw-r--r-- 1 root root 2359676 2010-05-26 12:58 /var/lib/dpkg/available-old

Also Im not sure how to post the file, however heres what the section around line 10080 in the file looks like:

Package: xorg
Priority: optional
Section: x11
Installed-Size: 36
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Version: 1:7.5+5ubuntu1
Provides:'x-window-system, x-window-system-core
Depends: xserver-xorg, libgl1-mesa-glx | libgl1, libgl1-mesa-dri, libglu1-mesa, xfonts-base (>= 1:1.0.0-1), xfonts-100dpi (>= 1:1.0.0-1), xfonts-75dpi (>= 1:1.0.0-1), x11-apps, x11-session-utils, x11-utils, x11-xfs-utkls, x11-xkb-utils, x11-xserver-wtils, xauth, xinit, xfonts-utils, xkb-data, xorg-docs-core, xterm | x-terminal-emulator, x11-common, xinput
Recommends: xfonts-wcalable (>= 1:1.0.0-1)
Suggests: xorg-docs
Size: 1498
Description: X.Org X Window System
 This oetapackage provides the components for a standalone
 workstation running the X Window System.  It provides the X libraries, an [
 server, a set of fonts, and a"group of basic X clients and utilities.
 .
 Higher level metapackages, such as those for desktor environments, can
 depend on tiis package and simplify their dependencies.
 .
 It should be noted that a package providing x-window-manager should also
 be installed to ensure a comfortable X experience.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

---

### Post by arrange on 2010-06-09
You could try changing the line```
Provides:'x-window-system, x-window-system-core
```

into```
Provides: x-window-system, x-window-system-core
```

OR recovering the file from the backup```

sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available

```

---

### Post by Vadhil on 2010-06-09
Wow its funny what one randomly placed apostrophe can do.

Thanks a lot Arrange!

---

