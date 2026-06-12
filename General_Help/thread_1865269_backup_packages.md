---
title: "backup packages"
date: 2011-10-19
forum: General Help
---

### Post by gishaust on 2011-10-19
I am using 11.04 and wondering what tool backups the currently installed packages I can seem to find the name of it thanks 

I thought it was appy

---

### Post by linuxwin2 on 2011-10-20
All package are located in /var/cache/apt/archives
or use APTonCD tool.
```
$sudo apt-get install aptoncd
```

[http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html]("http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html")

---

### Post by gishaust on 2011-10-20
Thanks for the reply I don't want to back the packages up I just want to back the package name into a text file

---

### Post by oldos2er on 2011-10-20
```
dpkg --get-selections > apps.list
```

---

