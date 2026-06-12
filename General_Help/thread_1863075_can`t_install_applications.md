---
title: "can`t install applications"
date: 2011-10-17
forum: General Help
---

### Post by Amgad elsaiegh on 2011-10-17
i tried to install Frostwire [the latest version] but the software center loads for little time the a pop-up message says failed to install shows up and here are the details 



> installArchives() failed: Selecting previously deselected package default-jre-headless.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 202834 files and directories currently installed.)
Unpacking default-jre-headless (from .../default-jre-headless_1%3a1.6-42ubuntu2_i386.deb) ...
Selecting previously deselected package default-jre.
Unpacking default-jre (from .../default-jre_1%3a1.6-42ubuntu2_i386.deb) ...
Setting up couchdb-bin (1.0.1-0ubuntu17) ...
groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 125 couchdb' returned error code 10. Exiting.
dpkg: error processing couchdb-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of desktopcouch-ubuntuone:
 desktopcouch-ubuntuone depends on desktopcouch (= 1.0.8-0ubuntu1); however:
  Package desktopcouch is not configured yet.
dpkg: error processing desktopcouch-ubuntuone (--configure):
 dependency problems - leaving unconfigured
Setting up default-jre-headless (1:1.6-42ubuntu2) ...
Setting up default-jre (1:1.6-42ubuntu2) ...
Errors were encountered while processing:
 couchdb-bin
 desktopcouch
 desktopcouch-ubuntuone
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up couchdb-bin (1.0.1-0ubuntu17) ...
groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 125 couchdb' returned error code 10. Exiting.
dpkg: error processing couchdb-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch-ubuntuone:
 desktopcouch-ubuntuone depends on desktopcouch (= 1.0.8-0ubuntu1); however:
  Package desktopcouch is not configured yet.
dpkg: error processing desktopcouch-ubuntuone (--configure):
 dependency problems - leaving unconfigured


any ideas ?

---

### Post by 2F4U on 2011-10-17
Did you try installing it from a terminal with apt-get?

---

### Post by Amgad elsaiegh on 2011-10-17
no, i can`t use terminal commands

**i tried many programs from the software center and all give me the same message

---

### Post by Amgad elsaiegh on 2011-10-18
i tried to install some software from synaptic but it gave me error too, 
here is a screenshot while i was installing Microsoft core fonts

[IMG]http://i793.photobucket.com/albums/yy211/amgadelsaiegh/forums/cantistallsoft.png[/IMG]

help would be appreciated

---

