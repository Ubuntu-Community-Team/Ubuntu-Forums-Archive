---
title: "Python Config trashed"
date: 2011-04-09
forum: General Help
---

### Post by gxwilson on 2011-04-09
This all started when my Screenlets stopped working. Then I noticed that my update notification stopped too.

So, to the command line I went to do and update hoping it was a recent update that needed to be fixed.

```
sudo apt-get update && sudo apt-get upgrade
```

It appears that multiple python packages are trashed some how??!??!

I've tried a lot of things and read a lot of posts and I'm not making any progress. 

Currently doing sudo apt-get -f install i get:

[HTML]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-configglue python-ubuntuone-client libimobiledevice0 python-ubuntuone-storageprotocol python-twisted-web python-pyinotify libcouchdb-glib-1.0-2
  python-protobuf libnb-platform11-java libswing-layout-java python-twisted-names protobuf-compiler libdesktopcouch-glib-1.0-2 libprotoc5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-bugbuddy python-desktopcouch python-desktopcouch-records python-evince python-evolution python-gnomeapplet python-gnomedesktop python-gnomekeyring
  python-gnomeprint python-gtop python-mediaprofiles python-metacity python-rsvg python-totem-plparser python-wnck
Suggested packages:
  bug-buddy
The following packages will be upgraded:
  python-bugbuddy python-desktopcouch python-desktopcouch-records python-evince python-evolution python-gnomeapplet python-gnomedesktop python-gnomekeyring
  python-gnomeprint python-gtop python-mediaprofiles python-metacity python-rsvg python-totem-plparser python-wnck
15 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
21 not fully installed or removed.
Need to get 0B/682kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 341445 files and directories currently installed.)
Preparing to replace python-gnomekeyring 2.30.0-0ubuntu1 (using .../python-gnomekeyring_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-gnomekeyring_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-desktopcouch 0.6.4-0ubuntu3.1 (using .../python-desktopcouch_0.6.4-0ubuntu3.2_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-desktopcouch-records 0.6.4-0ubuntu3.1 (using .../python-desktopcouch-records_0.6.4-0ubuntu3.2_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-wnck 2.30.0-0ubuntu1 (using .../python-wnck_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-wnck_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-bugbuddy 2.30.0-0ubuntu1 (using .../python-bugbuddy_2.30.0-0ubuntu1.1_all.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-bugbuddy_2.30.0-0ubuntu1.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-evince 2.30.0-0ubuntu1 (using .../python-evince_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-evince_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-evolution 2.30.0-0ubuntu1 (using .../python-evolution_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-evolution_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-gnomeapplet 2.30.0-0ubuntu1 (using .../python-gnomeapplet_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-gnomeapplet_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-gnomedesktop 2.30.0-0ubuntu1 (using .../python-gnomedesktop_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-gnomedesktop_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-gnomeprint 2.30.0-0ubuntu1 (using .../python-gnomeprint_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-gnomeprint_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-gtop 2.30.0-0ubuntu1 (using .../python-gtop_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-gtop_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-mediaprofiles 2.30.0-0ubuntu1 (using .../python-mediaprofiles_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-mediaprofiles_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-metacity 2.30.0-0ubuntu1 (using .../python-metacity_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-metacity_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-rsvg 2.30.0-0ubuntu1 (using .../python-rsvg_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-rsvg_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-totem-plparser 2.30.0-0ubuntu1 (using .../python-totem-plparser_2.30.0-0ubuntu1.1_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error processing /var/cache/apt/archives/python-totem-plparser_2.30.0-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
ValueError: bad marshal data
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-gnomekeyring_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3.2_all.deb
 /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3.2_all.deb
 /var/cache/apt/archives/python-wnck_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-bugbuddy_2.30.0-0ubuntu1.1_all.deb
 /var/cache/apt/archives/python-evince_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-evolution_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-gnomeapplet_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-gnomedesktop_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-gnomeprint_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-gtop_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-mediaprofiles_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-metacity_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-rsvg_2.30.0-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-totem-plparser_2.30.0-0ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

Please help

---

### Post by gxwilson on 2011-04-09
This is a very windows-ish kind of solution but; rebooting the machine cleared everything up :confused:

---

