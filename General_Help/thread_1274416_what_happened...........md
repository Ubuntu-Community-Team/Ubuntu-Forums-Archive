---
title: "what happened..........???"
date: 2009-09-24
forum: General Help
---

### Post by muctadir on 2009-09-24
i tried to install mc core fonts using this command-
sudo apt-get install msttcorefonts

but some thing odd happened. 

--2009-09-25 00:35:18--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-25 00:35:20--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-09-25 00:35:23--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Giving up.

--2009-09-25 00:35:28--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2009-09-25 00:35:31--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-09-25 00:35:33--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Giving up.

this thing appears in the terminal window for several times and at last the process ends printing this-

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on ttf-mscorefonts-installer; however:
  Package ttf-mscorefonts-installer is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
Setting up gsm-utils (1.10-13) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          chown: cannot access `/var/run/gsm-utils': No such file or directory
dpkg: error processing gsm-utils (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
 msttcorefonts
 gsm-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)



please can any one help me.

---

### Post by ddrichardson on 2009-09-24
It appears that Sourceforge have changed the file location, if you go there manually it redirects.

You need to raise a bug against the package:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/msttcorefonts](https://bugs.launchpad.net/ubuntu/jaunty/+source/msttcorefonts)

---

### Post by muctadir on 2009-09-24
actually just now i noticed that this problem happens when i try to install or remove any thing...

---

