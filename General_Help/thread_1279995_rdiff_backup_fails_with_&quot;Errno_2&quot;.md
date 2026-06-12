---
title: "rdiff backup fails with &quot;Errno 2&quot;"
date: 2009-10-01
forum: General Help
---

### Post by beaucoder on 2009-10-01
Hi Everyone, 

                                                                  Running Jaunty on Toshiba Satellite L305D. File system ext3.

Set up Keep backup system using Rdiff-backup. (Via Synaptic)

 How to fix?

 Fails with &quot;Errno 2&quot;. Exception '[Errno 2] No usable temporary directory found...

 in ['/tmp', '/var/tmp', '/usr/tmp', '/home/beaucoder']' raised of class '': File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 304, in error_check_Main try: Main(arglist) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 320, in Main Security.initialize(action or &quot;mirror&quot;, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 54, in initialize set_security_level(action, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 108, in set_security_level rdir = tempfile.gettempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 254, in gettempdir tempdir = _get_default_tempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 201, in _get_default_tempdir (&quot;No usable temporary directory found in %s&quot; % dirlist)) Traceback (most recent call last): File &quot;/usr/bin/rdiff-backup&quot;, line 30, in rdiff_backup.Main.error_check_Main(sys.argv[1:]) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 304, in error_check_Main try: Main(arglist) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 320, in Main Security.initialize(action or &quot;mirror&quot;, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 54, in initialize set_security_level(action, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 108, in set_security_level rdir = tempfile.gettempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 254, in gettempdir tempdir = _get_default_tempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 201, in _get_default_tempdir (&quot;No usable temporary directory found in %s&quot; % dirlist)) IOError: [Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/home/beaucoder']Exception '[Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/home/beaucoder']' raised of class '': File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 304, in error_check_Main try: Main(arglist) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 320, in Main Security.initialize(action or &quot;mirror&quot;, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 54, in initialize set_security_level(action, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 108, in set_security_level rdir = tempfile.gettempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 254, in gettempdir tempdir = _get_default_tempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 201, in _get_default_tempdir (&quot;No usable temporary directory found in %s&quot; % dirlist)) Traceback (most recent call last): File &quot;/usr/bin/rdiff-backup&quot;, line 30, in rdiff_backup.Main.error_check_Main(sys.argv[1:]) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 304, in error_check_Main try: Main(arglist) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Main.py&quot;, line 320, in Main Security.initialize(action or &quot;mirror&quot;, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 54, in initialize set_security_level(action, cmdpairs) File &quot;/var/lib/python-support/python2.6/rdiff_backup/Security.py&quot;, line 108, in set_security_level rdir = tempfile.gettempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 254, in gettempdir tempdir = _get_default_tempdir() File &quot;/usr/lib/python2.6/tempfile.py&quot;, line 201, in _get_default_tempdir (&quot;No usable temporary directory found in %s&quot; % dirlist)) IOError: [Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/home eaucoder']

 How to set up this &quot;temporary directory&quot;?

                                                                     Thanks  Ken

---

