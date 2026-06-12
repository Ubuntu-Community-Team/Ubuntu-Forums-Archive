---
title: "Unable to apt-get install"
date: 2006-06-22
forum: General Help
---

### Post by DoctorMO on 2006-06-22
I get the following error no matter what I try and install:

> 
sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
...
Setting up mplayer (0.99+1.0pre7try2+cvs20060117-0ubuntu8) ...

Errors were encountered while processing:
 libxml-libxml-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by johnc4510 on 2006-06-22
Try this to get rid of the error:
sudo apt-get install libxml-libxml-perl && libxml-simple-perl

---

### Post by DoctorMO on 2006-06-22
It didn't seem to work:

> 
sudo apt-get install libxml-libxml-perl && libxml-simple-perl
Reading package lists... Done
Building dependency tree... Done
libxml-libxml-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 99 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxml-libxml-perl (1.58-3) ...
update-perl-sax-parsers: Adding Perl SAX parser module info file of XML::LibXML::SAX::Parser...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-libxml-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not installed.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-libxml-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by DoctorMO on 2006-06-22
so I can't install anything, and perl is dead.

---

### Post by echo $USER on 2006-06-22
i cant really remember how it goes but try

sudo apt-get update -f

or

sudo apt-get install -f

basically something with the -f option.

---

### Post by bullfrog on 2006-06-22
try ubuntuguide.org  thats where i think i found it hope this helps

---

