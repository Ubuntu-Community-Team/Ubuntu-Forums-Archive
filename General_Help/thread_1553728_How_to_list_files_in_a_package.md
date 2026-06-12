---
title: "How to list files in a package"
date: 2010-08-15
forum: General Help
---

### Post by joycetipping on 2010-08-15
I've been trying to figure out whether the command-line tool "mysql" comes with mysql-server or mysql-client (I installed both at once, so I have no idea). It occurs to me that this is a good opportunity to learn more about linux package management.

I've tried saying "dpkg -L mysql-server", but it only lists the files in /usr/share/docs files for some reason. I'm sure there's got to be files elsewhere. Am I way off base?

Thanks!
Joyce

---

### Post by luigi_mb on 2010-08-15
If you have the deb package, do

```

dpkg -c package.deb

```

If not, and you have installed the package using Synaptic, in Synaptic highlight the package and click on Properties. In addition to other useful info, there will be a tab showing which files were installed where. 

/luigi

---

### Post by WorMzy on 2010-08-15
[mysql-client-core-5.1]("http://packages.ubuntu.com/lucid/i386/mysql-client-core-5.1/filelist").

It only lists the changelog and stuff for that package, because it's a dummy package that always depends on the most up-to-date version. The actual package would be [mysql-server-core-5.1]("http://packages.ubuntu.com/lucid/i386/mysql-server-core-5.1/filelist").

---

