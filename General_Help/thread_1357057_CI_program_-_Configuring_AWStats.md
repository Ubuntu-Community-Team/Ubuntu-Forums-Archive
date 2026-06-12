---
title: "CI program - Configuring AWStats"
date: 2009-12-16
forum: General Help
---

### Post by spikoley on 2009-12-16
I am setting up AWStats and the [directions]("https://help.ubuntu.com/community/AWStats#Configuration") use a command ci.  I checked the repositories and could not find it.  Google hasn't helped because the keyword is only 2 letters.  Any ideas?


> Configuration
Make a backup of apache2.conf
cd /etc/apache2
mkdir RCS (This is only necessary if you don't have an RCS directory installed there already.)
ci -l apache2.conf (check in the file before marking it up.)
Make a directory to correspond with the AWStats documentation and set it up:
cd /usr/local
mkdir awstats
cd awstats
cp -R /usr/share/doc/awstats/examples/*.* .
gunzip awstats.model.conf.gz
mkdir RCS
ci -l awstats.model.conf
mkdir wwwroot
mkdir wwwroot/cgi-bin

---

### Post by spikoley on 2009-12-17
I found the [package]("http://manpages.ubuntu.com/manpages/karmic/man1/ci.1.html").  It is called RCS in the repositories and the command is ci.

```
sudo apt-get install rcs
```

---

