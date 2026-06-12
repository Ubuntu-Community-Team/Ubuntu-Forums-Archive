---
title: "Gwibber error, cant remove gwibber"
date: 2010-02-17
forum: General Help
---

### Post by arnab_das on 2010-02-17
I'm using gwibber daily builds, however today while updating, the update manager showed that the gwibber update had failed.

when i tried to remove gwibber from the terminal using sudo apt-get remove gwibber, this is the error i get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gwibber is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-beaker python-mako python-pycurl python-egenix-mxtools
  gwibber-service python-gtkspell python-egenix-mxdatetime
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gwibber-service (2.29.1~bzr604-0ubuntu2~daily1~karmic) ...
Compiling /usr/lib/python2.6/dist-packages/gwibber/lib/__init__.py ...
Sorry: IndentationError: ('expected an indented block', ('/usr/lib/python2.6/dist-packages/gwibber/lib/__init__.py', 8, 101, '"""\nGwibberPublic is the public python class which provides convience methods \nfor using Gwibber.\n"""\n'))
pycentral: pycentral pkginstall: error byte-compiling files (38)
pycentral pkginstall: error byte-compiling files (38)
dpkg: error processing gwibber-service (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gwibber-service
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

how do i remove/reinstall gwibber?

---

### Post by arnab_das on 2010-02-17
solved it. that particular daily build of gwibber was to blame. removed myself from that (i mean deleted the repo for daily build that is).

now working fine! :)

but on the downside, am stuck with the old stable release of the boring old gwibber. :(

---

