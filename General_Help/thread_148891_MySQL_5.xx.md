---
title: "MySQL 5.xx"
date: 2006-03-22
forum: General Help
---

### Post by bardu on 2006-03-22
Hi all,

after a long time googleling I have found this source for MySQL 5.xx packages [http://www.dotdeb.org/mirrors]("http://www.dotdeb.org/mirrors") and added them to my /etc/apt/sources.list.

If I try to install MySQL 5.xx using Synaptic I get this warning:```
You are about to install software that can't be authenticated! Doing this could allow malicious individuals to damage or take control of your system.
```
For now I have cancelled the installation, but are in need of MySQL 5.xx.

Wondering whether someone has already used above mentioned source or whether there are other binary packages avaiable for MySQL 5.xx?

Thanks in advance.
Stephan

---

### Post by gos1 on 2006-03-22
I am usually accepting non authenticated software especially if I know what it is for. I did same thing for mysql and did not have any problems. So to me feel free to accept it.

---

### Post by adamkane on 2006-03-22
Dotdeb is for Debian. You can get away with installing simple Debian packages on Ubuntu, but not MySQL. You should remove the Dotdeb repository.

To install MYSQL5, see posts 15 and 29:
[http://www.ubuntuforums.org/showthread.php?t=80987](http://www.ubuntuforums.org/showthread.php?t=80987)

---

### Post by bardu on 2006-03-23
MySQL recommends to use the binary packages and instead of building them from source.
 
Okay, remains the question when Ubuntu is build on Debian why not use a Debian package?

Also, it seems to be converting MySQL 5.xx rpm packages to Debian packages using alien doesn't work well.

Stephan

---

### Post by adamkane on 2006-03-23
Ubuntu isn't Debian. You can only install Ubuntu Breezy packages on Ubuntu Btreezy, and you can only install Debian Sarge packages on Debian Sarge. If a Debian package happens to work on Ubuntu, it is a happy accident, but you will always be creating unresolvable conflicts within your code. Mixing packages isn't recommended, but sometimes it is possible, and doesn't have a huge negative impact.

MySQL is such a complicated package, that you can't force the Debian Sarge version to work with Ubuntu Breezy. An Ubuntu Dapper version may be converted to work with Ubuntu Breezy however, but there isn't a Dapper version available yet. The thread I posted earlier explains why the Dapper version isn't available yet, and if it does become available, it isn't likely to work with Breezy.

I guess the short answer is that MySQL 5 isn't even available for Debian. Some people have got it working on Debian, but it isn't available on the official Debian yet. Once it is available on official Debian, then it will become available on Ubuntu, although it is possible that Ubuntu will make it available first.

For now MySQL 4.1 is the latest version available for Ubuntu users.

Here is a list of Linux distributions that have MySQL 5 available.
[http://distrowatch.com/search.php?pkg=mysql&pkgver=5#pkgsearch]("http://distrowatch.com/search.php?pkg=mysql&pkgver=5#pkgsearch")

---

### Post by ZylGadis on 2006-03-23
I have been a happy user of dotdeb for a few months now. Their mysql5 is good for me (breezy). I have no idea if that is a coincidence or not, but it works well.

---

### Post by adamkane on 2006-04-01
MySQL5 HOWTO:
[https://wiki.ubuntu.com/MYSQL5FromSource](https://wiki.ubuntu.com/MYSQL5FromSource)

---

