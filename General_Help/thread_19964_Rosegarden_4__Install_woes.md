---
title: "Rosegarden 4  Install woes"
date: 2005-03-14
forum: General Help
---

### Post by nemesis101 on 2005-03-14
Hi,

Trying to install Rosegarden 4 (at release 0.9 or thereabouts - anyway a release that works in Mandrake when packaged as an RPM) but  :-? when I try and install the .deb package as located by search in Hoary Hedgehog I keep getting errors about libcurl - aparently it tries to do something with TWO versions of this and then one collides with the other!  I thought at first that removing from /usr/share/curl the "offending" file would be the answer, but apparently not, it seems that the Rosegarden install itself wants to install a file twise, from two different versions of libcurl? Any ideas folks? TA!

---

### Post by TheCondor on 2005-03-19
Im having this problem as well and I dont know how to solve it. Libcurl3 is installed but some applications ( such as the cd/dvd burning app graveman ) report that they need libcurl2 in order to be installed. ( they need vorbis-tools which in turn needs libcurl2 but then it all says libcurl2 cannot be installed ) 

Here is the log of apt

Selecting previously deselected package graveman.
(Reading database ... 143000 files and directories currently installed.)
Unpacking graveman (from .../graveman_0.3.8-1ubuntu0_i386.deb) ...
dpkg: dependency problems prevent configuration of graveman:
 graveman depends on vorbis-tools; however:
  Package vorbis-tools is not installed.
dpkg: error processing graveman (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 graveman
root@ubuntupc:/home/bill # apt-get install vorbis-tools
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  vorbis-tools: Depends: libcurl2 (>= 7.11.2-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntupc:/home/bill # apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcurl2 vorbis-tools
Suggested packages:
  libcurl2-gssapi ca-certificates
The following NEW packages will be installed:
  libcurl2 vorbis-tools
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/414kB of archives.
After unpacking 1266kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done     

Preconfiguring packages ...
Selecting previously deselected package libcurl2.
(Reading database ... Unpacking libcurl2 (from .../libcurl2_7.12.0.is.7.11.2-1ubuntu0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcurl2_7.12.0.is.7.11.2-1ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/share/curl/curl-ca-bundle.crt', which is also in package libcurl3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package vorbis-tools.
Unpacking vorbis-tools (from .../vorbis-tools_1.0.1-1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libcurl2_7.12.0.is.7.11.2-1ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
143078 files and directories currently installed.)


Thats what Ive been getting as the error report and I cant seem to figure it out. 

Any help would be greatly appreciated

---

