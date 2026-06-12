---
title: "Update Manager not working - error posted"
date: 2012-04-12
forum: General Help
---

### Post by Sternfan on 2012-04-12
Hi all,
I have a 10.04 PC that is not updating.  When I run update I get:

[B]Extracting templates from packages: 100%

Preconfiguring packages ...

(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:

 files list file for package 'libgtk2.0-common' is missing final newline

E: Sub-process /usr/bin/dpkg returned an error code (2)

A package failed to install.  Trying to recover:[/B]

Any ideas on how to solve?

Thanks,
Rob

---

### Post by raja.genupula on 2012-04-12
```
sudo cp -pr /var/lib/dpkg/info /var/lib/dpkg/info.backup
sudo rm /var/lib/dpkg/info/libgtk2.0-common.list
sudo aptitude -V reinstall libgtk2.0-common
```

do that in your terminal and try again all the best

---

### Post by Sternfan on 2012-04-12
OK - ran the first two lines = all good.  Ran the third line and got:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  libgtk2.0-common  
The following packages will be REMOVED:
  linux-headers-2.6.32-33{u} [2.6.32-33.72]  
  linux-headers-2.6.32-33-generic{u} [2.6.32-33.72]  
0 packages upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 73 not upgraded.
Need to get 0B of archives. After unpacking 85.5MB will be freed.
Do you want to continue? [Y/n/?] Y
E: I wasn't able to locate file for the libgtk2.0-common package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the libgtk2.0-common package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download[/B]

Any idea now?

Rob

---

### Post by raja.genupula on 2012-04-12
ok do this
```
sudo aptitude install libgtk2.0-common
```

---

### Post by Sternfan on 2012-04-12
Thanks!  That worked.

Rob

---

### Post by raja.genupula on 2012-04-12
please mark the thread as solved from thread tools . 
Thank you .

---

