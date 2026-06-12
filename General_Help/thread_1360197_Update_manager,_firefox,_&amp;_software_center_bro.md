---
title: "Update manager, firefox, &amp; software center broken after update"
date: 2009-12-20
forum: General Help
---

### Post by bgo544 on 2009-12-20
After update manager ran an update about 2 days ago, I restarted the system and found that firefox, update manager, and software center were no longer working.  There is also a persistent error warning from update notifier in the taskbar - "a problem occurred when checking for the updates".

Not sure what happened here, any ideas?

---

### Post by slakkie on 2009-12-20
Could you do the following:

```

sudo aptitude update
aptitude -s safe-upgrade

```

---

### Post by bgo544 on 2009-12-20
Got this output to the second part:

aptitude -s safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following partially installed packages will be configured:
  update-manager 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/784kB of archives. After unpacking 0B will be used.
Would download/install/remove packages.

---

### Post by slakkie on 2009-12-20
Could you now run it without the -s option (as root)?

---

### Post by bgo544 on 2009-12-20
Done, now it adds some error messages:

(Reading database ... 153517 files and directories currently installed.)
Preparing to replace update-manager 1:0.126.9 (using .../update-manager_1%3a0.126.9_all.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.126.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.126.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing update-manager (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

---

### Post by slakkie on 2009-12-21
This is not looking good.. 

Could you download the following package and install it:

[http://packages.ubuntu.com/karmic/all/update-manager/download](http://packages.ubuntu.com/karmic/all/update-manager/download)

dpkg -i <the_package.deb>

And retry the action.

BTW, I'm assuming you run karmic, if that is not the case, replace karmic in the download URL to your release (lsb_release -cs).

---

### Post by bgo544 on 2009-12-21
Ruh roh:

sudo dpkg -i update-manager_0.126.6_all.deb 
(Reading database ... 153517 files and directories currently installed.)
Preparing to replace update-manager 1:0.126.9 (using update-manager_0.126.6_all.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing update-manager_0.126.6_all.deb (--install):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 update-manager_0.126.6_all.deb

---

### Post by axthos on 2009-12-21
Hi, 
I'm having a very similar problem, in my case after an apparent bad update the system displays a persistent error:

[IMG]http://i.imgur.com/oDHFu.png[/IMG]

Doesn't matter whether I pick Show Updates / Install all updates / Check for updates... nothing will happen. 

I noticed Rythmbox and emesene stopped working. After more attempts running an update on aptitude an error kept being thrown after trying to update emesene. I thought uninstalling emesene completely at this point might be a good idea, but it wouldn't even let me do that. Synaptics package manager said I should reinstall before removing completely but that was another bad idea. It didn't let me.

After some other awful attempts and some new errors about some dependency error on jockey-common I tried installing it since apparently I did not have it and after running ***sudo apt-get install jockey-common***:

--- CODE ----
eythus@eythus:~$ aptitude -s safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  emesene jockey-common 
The following partially installed packages will be configured:
  jockey-gtk update-manager 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,632kB of archives. After unpacking 2,314kB will be used.
Do you want to continue? [Y/n/?] Y
Would download/install/remove packages.
eythus@eythus:~$ sudo aptitude  safe-upgrade
[sudo] password for eythus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  emesene jockey-common 
The following partially installed packages will be configured:
  jockey-gtk update-manager 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,632kB of archives. After unpacking 2,314kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 199329 files and directories currently installed.)
Preparing to replace emesene 1.5-1ubuntu1 (using .../emesene_1.5+r1731~ppakarmic1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/emesene_1.5+r1731~ppakarmic1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace jockey-common 0.5.5-0ubuntu2 (using .../jockey-common_0.5.5-0ubuntu3_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/jockey-common_0.5.5-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace update-manager 1:0.126.9 (using .../update-manager_1%3a0.126.9_all.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.126.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/emesene_1.5+r1731~ppakarmic1_i386.deb
 /var/cache/apt/archives/jockey-common_0.5.5-0ubuntu3_all.deb
 /var/cache/apt/archives/update-manager_1%3a0.126.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing jockey-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing emesene (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on jockey-common (= 0.5.5-0ubuntu3); however:
  Version of jockey-common on system is 0.5.5-0ubuntu2.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing update-manager (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 jockey-common
 emesene
 jockey-gtk
 update-manager
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

eythus@eythus:~$ 

---- END CODE -----

And yes I followed the instructions given to bgo544. I tried installing the package slakkie mentioned to no avail. This is the output from running 
```

sudo aptitude update
aptitude -s safe-upgrade
```

and then 
```
sudo aptitude safe-upgrade
```

Output:

```
eythus@eythus:~$ aptitude -s safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  emesene jockey-common 
The following partially installed packages will be configured:
  jockey-gtk update-manager 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,632kB of archives. After unpacking 2,314kB will be used.
Do you want to continue? [Y/n/?] Y
Would download/install/remove packages.
eythus@eythus:~$ sudo aptitude  safe-upgrade
[sudo] password for eythus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  emesene jockey-common 
The following partially installed packages will be configured:
  jockey-gtk update-manager 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,632kB of archives. After unpacking 2,314kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 199329 files and directories currently installed.)
Preparing to replace emesene 1.5-1ubuntu1 (using .../emesene_1.5+r1731~ppakarmic1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/emesene_1.5+r1731~ppakarmic1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 12, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace jockey-common 0.5.5-0ubuntu2 (using .../jockey-common_0.5.5-0ubuntu3_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/jockey-common_0.5.5-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace update-manager 1:0.126.9 (using .../update-manager_1%3a0.126.9_all.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.126.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/emesene_1.5+r1731~ppakarmic1_i386.deb
 /var/cache/apt/archives/jockey-common_0.5.5-0ubuntu3_all.deb
 /var/cache/apt/archives/update-manager_1%3a0.126.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing jockey-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: error processing emesene (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on jockey-common (= 0.5.5-0ubuntu3); however:
  Version of jockey-common on system is 0.5.5-0ubuntu2.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing update-manager (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 jockey-common
 emesene
 jockey-gtk
 update-manager
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

eythus@eythus:~$ 


```

Would it just be a plain better idea to just reinstall ubuntu? This is just giving me a headache.

Anyways, thanks for helping.

---

### Post by HappyFeet on 2009-12-21
> **axthos said:**
> 
Would it just be a plain better idea to just reinstall ubuntu? This is just giving me a headache.


A lot of people here take pride in fixing errors the "hard" way, and frown upon reinstalling. However, in a lot of instances it is better to just to reinstall and be done with it, instead of possibly waiting days for an answer. It is up to you. Good luck.

---

### Post by axthos on 2009-12-21
> **HappyFeet said:**
> A lot of people here take pride in fixing errors the "hard" way, and frown upon reinstalling. However, in a lot of instances it is better to just to reinstall and be done with it, instead of possibly waiting days for an answer. It is up to you. Good luck.

I know it is bad doing just that. Specially if the problem comes back later on. The only reason I'd rather wait some time for an answer is that I had an even harder time configuring my web server. Yeah I'm gonna keep searching for information on how to fix this.

---

### Post by slakkie on 2009-12-21
There are a couple of things you could do:

1) Create a bug report.
2) You could try to remove the package by dpkg: sudo dpkg -r --force-all update-manager. Then try reinstalling it with the .deb file you downloaded earlier. 

I've tried several things on my box to get the same result, but all upgrades and downgrades worked like a charm.

---

### Post by axthos on 2009-12-21
> **slakkie said:**
> There are a couple of things you could do:

1) Create a bug report.
2) You could try to remove the package by dpkg: sudo dpkg -r --force-all update-manager. Then try reinstalling it with the .deb file you downloaded earlier. 

I've tried several things on my box to get the same result, but all upgrades and downgrades worked like a charm.

About #2:

Same results:
----- CODE -------
eythus@eythus:~$ sudo dpkg -r --force-all update-manager
[sudo] password for eythus: 
dpkg: status database area is locked by another process
eythus@eythus:~$ sudo dpkg -r --force-all update-manager
dpkg: update-manager: dependency problems, but removing anyway as you requested:
 ubuntu-desktop depends on update-manager.
 update-notifier depends on update-manager; however:
  Package update-manager is to be removed.
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 199328 files and directories currently installed.)
Removing update-manager ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 7, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error processing update-manager (--remove):
 subprocess installed pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 4, in <module>
    from optparse import OptionParser
  File "/usr/lib/python2.6/optparse.py", line 90, in <module>
    from gettext import gettext
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 update-manager
eythus@eythus:~$ 
----- /CODE ------

---

### Post by bgo544 on 2009-12-21
Yeah, same exact output for me when trying the forced removal of update manager.

---

### Post by axthos on 2009-12-21
Well uhm, I tried and all but then gave up and continued with my usual programming. All of a sudden amsn crashed and right after that I was not able to view any content in any window. As in... it worked... I blindly typed in sudo killall wish8.5 (amsn process) and it worked, but nothing was displayed on any screen... I restarted ubuntu... and that was it. It couldn't mount any drive.

I'm on ubuntu live cd right now... And I have no other means to backup my information... if I install the same version of ubuntu will my hard drive be erased or will it just overwrite certain files? 

I really have no other way of backing up my files and I really gotta keep on working since i'm on a deadline. Any suggestions are entirely welcome. Thanks to everyone.

---

### Post by FourthAndVine on 2009-12-22
Sorry, double-post.

---

### Post by FourthAndVine on 2009-12-22
Just piling on... I'm having the exact same problem after running some updates on the 21st that updated python and libpython.

```
root@pea:/usr/bin# python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gettext
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/gettext.py", line 49, in <module>
    import locale, copy, os, re, struct, sys
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/gettext.py", line 49, in <module>
    import locale, copy, os, re, struct, sys
EOFError: EOF read where object expected
>>> 

```

Has a bug report been made about this? Unfortunately I'm not in a position to reinstall until a week or two from now. I'm kind of worried this update just managed to bork all of python, rendering the system somewhat un-fixable, which would be a bad thing for my productivity over the coming two weeks.

---

### Post by FourthAndVine on 2009-12-22
Update...

Heh, overcome by a sense of panic I checked out locale.py, copy.py, os.py, re.py, struct.py and gettext.py, added newlines at the end of the files and voila, problem gone.

This newline problem, is it something unique to an encoding setting on my machine, or is it a problem with the update that got pushed out? If it's the latter, I'm surprised more people haven't seen this. There are probably other newlines that need to be added but the above lets me run updates again so if an update should get pushed out it will work at least.

Update to the Update...

I've taken a look at an example (threading.py) in the old (python2.6_2.6.4~rc2-0ubuntu1_i386) and new (python2.6_2.6.4-0ubuntu3_i386) packages, but the old doesn't have a newline either, so I'm not sure what caused the change. The changelog for the new package indicates a change to some encoding-related things, maybe that's the problem? I think I've exhausted my sleuthing for now.

---

### Post by bgo544 on 2009-12-22
The newline thing with the .py files did not work at all for me.

---

