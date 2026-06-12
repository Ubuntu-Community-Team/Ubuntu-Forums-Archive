---
title: "Problem installing software on ubuntu from the ubuntu software center"
date: 2009-12-18
forum: General Help
---

### Post by KheldarJ on 2009-12-18
Hey,
while trying to download and install software on ubuntu ( i have 9.10 ), i get this message:

The installation or removal of a software package failed.

I click on details, and this is what i get. It happens to me every time i try installing a software via the ubuntu software center.
can anyone help me solve the problem? thanks!

> 
installArchives() failed: Selecting previously deselected package tetzle. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 147508 files and directories currently installed.) 
Unpacking tetzle (from .../tetzle_1.2.1-1_i386.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Setting up ttf-mscorefonts-installer (3.0) ... 
 
These fonts were provided by Microsoft "in the interest of cross- 
platform compatibility".  This is no longer the case, but they are 
still available from third parties. 
 
You are free to download these fonts and use them for your own use, 
but you may not redistribute them in modified form, including changes 
to the file name or packaging format. 
 
--2009-12-18 18:19:13--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-18 18:19:23--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving switch.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `switch.dl.sourceforge.net' 
--2009-12-18 18:19:33--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving mesh.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `mesh.dl.sourceforge.net' 
--2009-12-18 18:19:43--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving dfn.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `dfn.dl.sourceforge.net' 
--2009-12-18 18:19:53--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving heanet.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `heanet.dl.sourceforge.net' 
--2009-12-18 18:20:03--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving jaist.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `jaist.dl.sourceforge.net' 
--2009-12-18 18:20:14--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving nchc.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `nchc.dl.sourceforge.net' 
--2009-12-18 18:20:24--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `ufpr.dl.sourceforge.net' 
--2009-12-18 18:20:34--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving internode.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `internode.dl.sourceforge.net' 
--2009-12-18 18:20:44--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving voxel.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `voxel.dl.sourceforge.net' 
--2009-12-18 18:20:54--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving kent.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `kent.dl.sourceforge.net' 
--2009-12-18 18:21:04--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving internap.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `internap.dl.sourceforge.net' 
sha256sum: andale32.exe: No such file or directory 
andale32.exe: FAILED open or read 
sha256sum: WARNING: 1 of 1 listed file could not be read 
Checksum mismatch for andale32.exe, aborting! 
dpkg: error processing ttf-mscorefonts-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up tetzle (1.2.1-1) ... 
 
Errors were encountered while processing: 
 ttf-mscorefonts-installer

---

### Post by howefield on 2009-12-18
Try downloading the package here and double click your downloaded file to start the install.

[http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer](http://packages.ubuntu.com/karmic/ttf-mscorefonts-installer)

---

### Post by KheldarJ on 2009-12-19
Installing the package failed. They show me terminal with nearly the same message as the one i posted before.
what's happening?

---

### Post by KheldarJ on 2009-12-19
While updating ubuntu, i get this message as well:
E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1
it seems that there's a problem with installing the mscorefonts. and for some reason, the problem stops me from installing all the other software i download from the ubuntu software center.
PLEASE HELP!! WHAT SHOULD I DO??

---

