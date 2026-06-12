---
title: "dpkg of compiled program"
date: 2012-03-16
forum: General Help
---

### Post by IlluminatiBG on 2012-03-16
I use ubuntu 11.10 from relatively a month, so I'm still quite new (learn how to do some thing by searching in google).
However I couldn't find something.
I downloaded last version (source) of apache and php and compiled it successfully. Now it is placed in /usr/local/apache2
However nothing is shown in dpkg, neither in dpkg -l, nor by dpkg --get-selections. Is it possible and if yes, how to tell ubuntu, that apache is installed?

---

### Post by oldos2er on 2012-03-16
When you install an app from source, you're completely bypassing the APT system, so neither dpkg nor any of the other package managers know about what you've installed. One way of dealing with that is to use 'checkinstall', see [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Is there some particular reason you compiled apache instead of installing it from the repositories?

---

### Post by IlluminatiBG on 2012-03-17
To the question:

```
$ sudo apt-get update
$ apt-cache show apache2
Version: 2.2.20-1ubuntu1
``````
$ httpd -v
Server version: Apache/2.4.1 (Unix)
```Anyway thanks for help, I've installed checkinstall :)

---

