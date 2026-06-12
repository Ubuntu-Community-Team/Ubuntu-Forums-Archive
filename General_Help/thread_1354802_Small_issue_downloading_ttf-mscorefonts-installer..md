---
title: "Small issue downloading ttf-mscorefonts-installer....?"
date: 2009-12-14
forum: General Help
---

### Post by r2rX on 2009-12-14
Greetz guys,

Alrighty, in a prior attempt to configure my network, I was recommended to install a package called webmin. In the process of installing it, it required the ttf-mscorefonts-installer to be installed....but, for some reason, it refuses to download from any of the mirrors available. As a result, any other package I want to install (i.e. Wine, Thunderbird 3.0 etc) has issues downloading as the fonts are queued at all times and the package manager wants to complete downloading these fonts...which it can't.

So is there a way to cancel it? Cause I cannot install ANYTHING else until it's done.

This is the error:
```
$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-14 17:16:10--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-14 17:16:20--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2009-12-14 17:16:30--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-14 17:16:40--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-12-14 17:16:50--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-12-14 17:17:00--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-14 17:17:10--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-12-14 17:17:20--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-12-14 17:17:30--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-12-14 17:17:40--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-12-14 17:17:50--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-14 17:18:00--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any advice is appreciated greatly. ;)

EDIT: Alright, I managed to solve this issue. It seems that the issue stems from an error within the Synaptic Package Manager (that has been present since Ubuntu 9.04).....so someone found a work-around for it.

[http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

So it works sweet! :)

r2rX  :D

---

### Post by audiomick on 2009-12-14
Hallo.
You have noticed that the connection is timing out?
I can't tell you how to fix it, I'm sorry, but I would suspect more a problem with the internet connection than one with the package in question.

---

### Post by r2rX on 2009-12-14
Alright, I managed to solve this issue. It seems that the issue stems from an error within the Synaptic Package Manager (that has been present since Ubuntu 9.10).....so someone found a work-around for it.

[http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

So it works sweet! :D

r2rX  :D

---

### Post by fnmblot on 2009-12-16
sudo apt-get install pdns-recursor

Problem resolved! :-D

---

### Post by sakiland on 2009-12-20
Try [this]("http://www.james-blogs.com/2009/11/20/fixing-the-ttf-mscorefonts-package-in-ubuntu-9-10/"), works for me.

[http://www.james-blogs.com/2009/11/20/fixing-the-ttf-mscorefonts-package-in-ubuntu-9-10/](http://www.james-blogs.com/2009/11/20/fixing-the-ttf-mscorefonts-package-in-ubuntu-9-10/)

---

### Post by r2rX on 2009-12-21
Cheers for the info, guys. ;)

r2rX  :D

---

### Post by r2rX on 2009-12-24
Alright. Even with the procedure, from the site recommended by sakiland, the only one that works is the fix that I refered to.

Thanks for the assistance, guys. ;)

r2rX  :D

---

### Post by christ0pher0 on 2009-12-31
Thanks so much!  Your fix was perfect.  Happy New Year :P

---

### Post by James2k on 2010-01-31
Ha ha ha thanks [sakiland]("http://ubuntuforums.org/member.php?u=981253") for referencing my blog post :P

The problem and it's fix seems to be different for some people, however in most cases it seems adding different download mirrors to the hosts file will get the job done.

---

