---
title: "Where do my installed packages go?"
date: 2011-10-23
forum: General Help
---

### Post by theomer1 on 2011-10-23
I am very new to Linux. I just installed Ubuntu 11.10 Server. I then installed nginx using this command:
```
sudo apt-get install nginx
```
Now I can't find where it got installed. According to nginx's wiki ([http://wiki.nginx.org/GettingStarted#Running_Nginx](http://wiki.nginx.org/GettingStarted#Running_Nginx)), I should be able to locate it in /var/run but it's not there.

---

### Post by matt_symes on 2011-10-23
Hi

dpkg -L <package_name> will tell you where the files for a package are installed.
```

matthew@matthew-Aspire-7540:~$ dpkg -L htop
/.
/usr
/usr/bin
/usr/bin/htop
/usr/share
/usr/share/applications
/usr/share/applications/htop.desktop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/htop.1.gz
/usr/share/pixmaps
/usr/share/pixmaps/htop.png
/usr/share/doc
/usr/share/doc/htop
/usr/share/doc/htop/AUTHORS
/usr/share/doc/htop/README
/usr/share/doc/htop/copyright
/usr/share/doc/htop/changelog.Debian.gz
/usr/share/menu
/usr/share/menu/htop
matthew@matthew-Aspire-7540:~$
```

Kind regards

---

