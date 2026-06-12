---
title: "Difficulty installing OpenOffice"
date: 2012-08-07
forum: General Help
---

### Post by thedoctor81877 on 2012-08-07
Hullo all. I need to install OpenOffice (I know LibreOffice is now the default, but I specifically need Open Office for a new job - long story) and I tried via the ppa for Open Office 
and got this;


Unpacking openoffice (from .../openoffice_3.4~precise_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice_3.4~precise_i386.deb (--unpack):
 trying to overwrite '/usr/share/mimelnk/application/openoffice.org3-ms-powerpoint-presentation.desktop', which is also in package openoffice.org-debian-menus 3.4-9590
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice_3.4~precise_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be greatly appreciated. Unfortunately, I am somewhat on a time constraint. Thanks a bunch!

---

### Post by daslinkard on 2012-08-07
This [link]("http://www.fossapps.com/2011/12/01/how-to-install-openoffice-in-ubuntu-11-10/") seems to have a pretty good explanation.

---

### Post by thedoctor81877 on 2012-08-07
Thanks, I shall try that once I can download that size of a file (I cannot do so at present, but later on I will be able to). I will let you know how it goes. Thanks again!

---

### Post by vexorian on 2012-08-07
> **thedoctor81877 said:**
> Hullo all. I need to install OpenOffice (I know LibreOffice is now the default, but I specifically need Open Office for a new job - long story) and I tried via the ppa for Open Office 
and got this;


Unpacking openoffice (from .../openoffice_3.4~precise_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice_3.4~precise_i386.deb (--unpack):
 trying to overwrite '/usr/share/mimelnk/application/openoffice.org3-ms-powerpoint-presentation.desktop', which is also in package openoffice.org-debian-menus 3.4-9590
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice_3.4~precise_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be greatly appreciated. Unfortunately, I am somewhat on a time constraint. Thanks a bunch!
Do you really need open office for the job. Unless the job is open office developer... I mean, at this time they are basically the same thing with different logo.

---

### Post by thedoctor81877 on 2012-08-07
The link provided above did indeed work. Thanks again!

---

### Post by thedoctor81877 on 2012-08-07
OK - this is what I am trying to accomplish (and so far in AOO, this is not working - but before switching back I need to know it will work in LO) - I need to be able embedd Math Type objects into AOO (Or LO) as an OLE by insert -> OLE Object -> Create New -> Object Type -> Create New 

but in AOO, under OLE Object, I do not see Create New under Object Type at all. 

When I installed AOO, I did get the following:

Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

Could this be part of the problem? Thanks for any help.

---

### Post by thedoctor81877 on 2012-08-07
When I cd into desktop integration and type   

sudo dpkg -i *.deb

I get the following:


Errors were encountered while processing:
 openoffice.org3.4-debian-menus_3.4-9590_all.deb

Help please!

---

### Post by Hagar Delest on 2012-08-08
We need the whole error message, usually, there is other lines. Make sure that all the LibO packages have been removed. See also: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Note that if you install AOO and LibO with their deb packages, they can run in parallel (but not if you use the Ubuntu version from the software center).

---

