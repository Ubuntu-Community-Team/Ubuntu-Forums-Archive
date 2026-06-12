---
title: "Move /var and /tmp to one partition"
date: 2010-03-24
forum: General Help
---

### Post by carloskar on 2010-03-24
Hello!
I have installed Ubuntu 9.10 Server on a flash based USB memory stick, so I wanted to move /var and /tmp to a partition on a hard drive (one partition with both /var and /tmp and symlinks from / to those). I read this guide here [http://www.gentoo.org/doc/en/articles/partitioning-p2.xml](http://www.gentoo.org/doc/en/articles/partitioning-p2.xml) but it failed after restarting the server. I then found out that ubuntu must have /var/run on the root file system ([http://utcc.utoronto.ca/~cks/space/blog/linux/UbuntuVarRun]("http://utcc.utoronto.ca/%7Ecks/space/blog/linux/UbuntuVarRun")) so that was why it did not work.

My workaround for this was to create /var and /var/run on the root file system, mount my partition to /var and then symlink /tmp to /var/temp. It now works as I wanted, both /var and /tmp on the same partition. But is there a better way to solve this? Can there be any problems with /tmp->/var/temp?

thanks!

---

### Post by carloskar on 2010-03-27
I bumped into one problem with having /tmp->/var/temp, I had to enable read/write for /var/temp in apparmor for mysql, and will probably have to do the same for every other application?

```
$ ls -l / | grep tmp
lrwxrwxrwx   1 root root     9 2010-03-25 03:34 tmp -> /var/temp
$ ls -l /var | grep temp
drwxrwxrwt 12 root root       4096 2010-03-27 21:32 temp
```Is there a way to tell apparmor to don't care about a directory? I suspect that something like that has to exist for the default /tmp.

---

### Post by carloskar on 2010-03-27
> **carloskar said:**
> Is there a way to tell apparmor to don't care about a directory? I suspect that something like that has to exist for the default /tmp.
Answering myself, yes there is in /etc/apparmor.d/abstractions/user-tmp, changing both entries for /tmp to /var/temp fixes the problem.

---

### Post by sundman on 2013-01-09
AppArmor also has an alias mechanism, too that resides in /etc/apparmor.d/tunables/alias.

E.g. and note the comma at the end of the line

```

alias /var/ -> /data/var/,

```

---

