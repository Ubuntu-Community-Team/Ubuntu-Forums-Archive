---
title: "Lexmark Installer wants Cups 1.2 on Hardy"
date: 2009-07-03
forum: General Help
---

### Post by afrodeity on 2009-07-03
After waiting about four months for a working 8.04 64 installer for my Lexmark X2650, the @#$% thing wants Cups 1.2

I couldn't find cups, but found cupsys using 'sudo aptitude show cupsys'

Here is the ouput

```

Package: cupsys
State: installed
Automatically installed: yes
Version: 1.3.7-1ubuntu3.5
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 10.2M
Depends: adduser, cupsys-common, debconf (>= 1.2.9) | debconf-2.0, ghostscript |
        gs-esp, libavahi-compat-libdnssd1 (>= 0.6.13), libc6 (>= 2.4),
        libcupsimage2 (>= 1.3.0), libcupsys2 (>= 1.3.4), libdbus-1-3 (>=
        1.1.1), libgnutls13 (>= 2.0.4-0), libkrb53 (>= 1.6.dfsg.2),
        libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libpaper1, libslp1,
        lsb-base (>= 3), perl-modules, poppler-utils | xpdf-utils, procps,
        ssl-cert (>= 1.0.11)
Recommends: avahi-utils, cupsys-client, foomatic-filters, smbclient (>= 3.0.9)
Suggests: cups-pdf, cupsys-bsd, cupsys-driver-gutenprint, foomatic-filters-ppds,
         hplip, xpdf-korean | xpdf-japanese | xpdf-chinese-traditional |
         xpdf-chinese-simplified
Conflicts: cupsys-pstoraster (< 2)
Replaces: cupsys-pstoraster
Description: Common UNIX Printing System(tm) - server
The Common UNIX Printing System (or CUPS(tm)) is a printing system and general
replacement for lpd and the like.  It supports the Internet Printing Protocol
(IPP), and has its own filtering driver model for handling various document
types.

This package provides the CUPS scheduler/daemon and related files.

The terms "Common UNIX Printing System" and "CUPS" are trademarks of Easy
Software Products (www.easysw.com), and refer to the original source packages
from which these packages are made.

```

What should I do?

---

### Post by nathan726 on 2009-07-31
Does this link help: [http://ubuntuforums.org/showthread.php?p=7713382#post7713382](http://ubuntuforums.org/showthread.php?p=7713382#post7713382)

---

