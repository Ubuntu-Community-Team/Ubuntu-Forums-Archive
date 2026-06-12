---
title: "Phoronix test suite &quot;bad quality package&quot;"
date: 2011-06-04
forum: General Help
---

### Post by brad1138 on 2011-06-04
I installed "Phoronix test suite" from the standard Ubuntu SPM repositories. It crashes on launch. I found that that is a bug explained here: [bug 641268]("https://bugs.launchpad.net/ubuntu/+source/phoronix-test-suite/+bug/641268").

The fix is: "You need to manually install PHP5-GTK from source or one of the packages I have provided elsewhere or to just use the command-line interface, but PHP5-GTK is not packaged for Ubuntu (see LP #260235). This is also a duplicate of LP #430946."

When I downloaded and tried to install PHP5-GTK through the Software Center I get this message:

> "The package is of bad quality"

The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

Lintian check results for /home/brad/Downloads/php5-gtk-2.0.1~2010-05-11_i386.deb:
E: php5-gtk: wrong-file-owner-uid-or-gid etc/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid etc/php5/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid etc/php5/conf.d/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid etc/php5/conf.d/cairo.ini 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid etc/php5/conf.d/php_gtk2.ini 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid usr/lib/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid usr/lib/php5/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid usr/lib/php5/20090626+lfs/ 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid usr/lib/php5/20090626+lfs/cairo.so 1000/1000
E: php5-gtk: wrong-file-owner-uid-or-gid usr/lib/php5/20090626+lfs/php_gtk2.so 1000/1000


It gives me an option to ignore this message and install anyway. What should I do?

Thank you,
Brad

---

