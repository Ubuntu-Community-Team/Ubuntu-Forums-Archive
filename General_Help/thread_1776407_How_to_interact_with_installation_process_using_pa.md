---
title: "How to interact with installation process using package manager?"
date: 2011-06-06
forum: General Help
---

### Post by rdh61 on 2011-06-06
Hi,

I have been trying to install an electronic medical records package (openemr) using package manager on Ubuntu 10.10. The installation requires that I give answers to certain questions. In 9.10 and 10.04, one could follow the installation and interact, if necessary, by opening a terminal within package manager. This option seems not to be available in 10.10. Have I missed something?

Many thanks.

---

### Post by btindie on 2011-06-06
Are you trying to install the tar.gz or the deb file? 

TAR.GZ: Have you read through the installation instructions here? - [http://wiki.oemr.org/wiki/OpenEMR_4.0_Linux_Installation](http://wiki.oemr.org/wiki/OpenEMR_4.0_Linux_Installation) Do you have the required dependencies?

DEB: Have you read these instructions? [http://wiki.oemr.org/wiki/OpenEMR_4.0_Ubuntu-Debian_Package_Installation](http://wiki.oemr.org/wiki/OpenEMR_4.0_Ubuntu-Debian_Package_Installation) Try doing the commandline Ubuntu install method.

---

### Post by rdh61 on 2011-06-06
Hi btindie,

Thanks for your reply. I've been trying to install the deb file (actually version 3.2).

I tried with the command line, following the wiki instructions at [http://wiki.oemr.org/wiki/OpenEMR_3.2_Ubuntu-Debian_Package_Installation](http://wiki.oemr.org/wiki/OpenEMR_3.2_Ubuntu-Debian_Package_Installation) , but the installation failed:

robert@robert-workdesk:~$ wget downloads.sourceforge.net/openemr/openemr_3.2.0-1_all.deb
--2011-06-05 10:36:12--  [http://downloads.sourceforge.net/openemr/openemr_3.2.0-1_all.deb](http://downloads.sourceforge.net/openemr/openemr_3.2.0-1_all.deb)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb](http://downloads.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb) [following]
--2011-06-05 10:36:12--  [http://downloads.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb](http://downloads.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://puzzle.dl.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb](http://puzzle.dl.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb) [following]
--2011-06-05 10:36:12--  [http://puzzle.dl.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb](http://puzzle.dl.sourceforge.net/project/openemr/OpenEMR%20Ubuntu_debian%20Package/3.2.0/openemr_3.2.0-1_all.deb)
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 61579226 (59M) [application/octet-stream]
Saving to: `openemr_3.2.0-1_all.deb.1'

100%[======================================>] 61,579,226  14.4K/s   in 68m 18s 

2011-06-05 11:44:33 (14.7 KB/s) - `openemr_3.2.0-1_all.deb.1' saved [61579226/61579226]

robert@robert-workdesk:~$ sudo aptitude update
[sudo] password for robert: 
sudo: aptitude: command not found
robert@robert-workdesk:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 329 not upgraded.
robert@robert-workdesk:~$ sudo dpkg -i openemr_3.2.0-1_all.deb
Selecting previously deselected package openemr.
(Reading database ... 118317 files and directories currently installed.)
Unpacking openemr (from openemr_3.2.0-1_all.deb) ...
dpkg-deb (subprocess): short read on buffer copy for failed to write to pipe in copy
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing openemr_3.2.0-1_all.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./var/www/openemr/sql/DBC_sql_statements/cl_prestatiecode.sql.gz'
postrm asked to do abort-install
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 openemr_3.2.0-1_all.deb
robert@robert-workdesk:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 329 not upgraded.
robert@robert-workdesk:~$  sudo dpkg -i openemr_3.2.0-1_all.deb
(Reading database ... 118317 files and directories currently installed.)
Unpacking openemr (from openemr_3.2.0-1_all.deb) ...
dpkg-deb (subprocess): short read on buffer copy for failed to write to pipe in copy
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing openemr_3.2.0-1_all.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./var/www/openemr/sql/DBC_sql_statements/cl_prestatiecode.sql.gz'
postrm asked to do abort-install
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 openemr_3.2.0-1_all.deb
robert@robert-workdesk:~$

---

### Post by btindie on 2011-06-06
It looks like there may be an error in the file you downloaded, check the md5sum to see if it's corrupt or not. It should be c234e4ad51574d95e75b7b09b1bae4a8, which I got from [http://sourceforge.net/projects/openemr/files/OpenEMR%20Ubuntu_debian%20Package/3.2.0/](http://sourceforge.net/projects/openemr/files/OpenEMR%20Ubuntu_debian%20Package/3.2.0/) If that fails then just download it again, otherwise it may be that it doesn't work with your version of Ubuntu and might stand a better chance using v4. It's not something I've used before.

---

