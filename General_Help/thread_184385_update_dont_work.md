---
title: "update dont work"
date: 2006-05-29
forum: General Help
---

### Post by zigoto on 2006-05-29
hi
I have installed drapper and when i click to update on software actualization, this dont work,  and show a error saying that is not possible, and says that the repository can not be able or a problem with the network connection.

Repository
> 
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 403 Forbidden
[http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 403 Forbidden

what can i do? Install in english? I have installed in portuguese !

---

### Post by Sutekh on 2006-05-29
You most likely have a problem with the fact that your repositories are *local *ones.

In other words, they are **pt.archive.ubuntu**.  Those local servers may be down or re-shuffling with Dapper coming up.

You could try removing the local **pt.** part and use the main Ubuntu repositories.

First copy your sources to a backup before editing
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
``` The sources will currently look like
```
deb http://**pt.**archive.ubuntu.com/ubuntu/ dapper main restricted
``` All you need to do is remove the **pt.** parts from each line (dont forget the .)

When you are done they should look like
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
``` and so on.

Save the file and use
```
sudo apt-get update
```to refresh the repositories

---

