---
title: "File not found after download"
date: 2010-09-10
forum: General Help
---

### Post by waloshin on 2010-09-10
$ wget [http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download](http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download)
--2010-09-10 02:25:09--  [http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download](http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb?r=&ts=1284107119&use_mirror=iweb](http://downloads.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb?r=&ts=1284107119&use_mirror=iweb) [following]
--2010-09-10 02:25:19--  [http://downloads.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb?r=&ts=1284107119&use_mirror=iweb](http://downloads.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb?r=&ts=1284107119&use_mirror=iweb)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://iweb.dl.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb](http://iweb.dl.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb) [following]
--2010-09-10 02:25:30--  [http://iweb.dl.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb](http://iweb.dl.sourceforge.net/project/webadmin/webmin/1.520/webmin_1.520_all.deb)
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14607442 (14M) [application/x-debian-package]
Saving to: `download'


Sudo dpkg -i webmin_1.520_all.deb
dpkg: error processing webmin_1.520_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 webmin_1.520_all.deb

---

### Post by GregBrannon on 2010-09-10
Are you sure the file names match?  I see 'weba..' in your download but 'webm..' in your sudo command.

---

### Post by spjackson on 2010-09-10
> **waloshin said:**
> 
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14607442 (14M) [application/x-debian-package]
Saving to: `download'

As it says, the file is called download. Rename it to the real thing.

---

### Post by waloshin on 2010-09-10
> **spjackson said:**
> As it says, the file is called download. Rename it to the real thing.

Thanks sometimes... anyways yeah just running sudo dpkg -i download worked.

---

