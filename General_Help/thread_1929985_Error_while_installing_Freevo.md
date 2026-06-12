---
title: "Error while installing Freevo"
date: 2012-02-22
forum: General Help
---

### Post by bludshot on 2012-02-22
I tried to install freevo with synaptic but I got the following errors (from the install log):

(Everything above this appeared to be fine to me)
```
Setting up python-kaa-metadata (0.7.7-2build1) ...
Processing triggers for python-twisted-core ...
Setting up python-twisted (11.0.0-2) ...
Processing triggers for python-central ...
Setting up python-freevo (1.9.0-10.1ubuntu1) ...
Setting up freevo (1.9.0-10.1ubuntu1) ...
Gtk-WARNING **: cannot open display:  at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
debconf: unable to initialize frontend: Gnome
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
Adding group `freevo' (GID 118) ...
Done.
Adding user  'freevo'.
Adding user freevo to group cdrom
Adding user freevo to group audio
Adding user freevo to group plugdev
Traceback (most recent call last):
  File "/usr/bin/freevo.real", line 521, in <module>
    execfile(freevo_version, {}, versions)
IOError: [Errno 2] No such file or directory: '/usr/lib/pymodules/python2.5/freevo/version.py'
dpkg: error processing freevo (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 freevo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up freevo (1.9.0-10.1ubuntu1) ...
Gtk-WARNING **: cannot open display:  at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
debconf: unable to initialize frontend: Gnome
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
Traceback (most recent call last):
  File "/usr/bin/freevo.real", line 521, in <module>
    execfile(freevo_version, {}, versions)
IOError: [Errno 2] No such file or directory: '/usr/lib/pymodules/python2.5/freevo/version.py'
dpkg: error processing freevo (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 freevo

```


Then if I try to run freevo nothing happens. What can I do to fix this? Looks like pretty specific errors to me

Thanks!

---

### Post by bludshot on 2012-02-22
almoxarife on #ubuntu pointed out the solution to this here: [http://ubuntuforums.org/showthread.php?p=10825057#post10825057](http://ubuntuforums.org/showthread.php?p=10825057#post10825057)

---

