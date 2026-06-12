---
title: "vhosts default"
date: 2010-12-27
forum: General Help
---

### Post by christophweise on 2010-12-27
Hi everybody,

I accidently deleted my default and default-ssl files in the sites-available directory. Can somebody post the content? That would be great.

Thanks in advance.

Christoph

---

### Post by gmargo on 2010-12-27
I could post the content, but instead I'll show you how to recover them yourself.


[LIST=1]
[*]What package are they from?
```

$ dpkg -S /etc/apache2/sites-available/default
apache2.2-common: /etc/apache2/sites-available/default
$ dpkg -S /etc/apache2/sites-available/default-ssl
apache2.2-common: /etc/apache2/sites-available/default-ssl

```
[*]Download fresh copy of **apache2.2-common** .deb file. (-d flag says download only)
```

$ sudo aptitude -d -V reinstall apache2.2-common

```
[*]Make a temp directory and extract .deb file into it. Adjust filename if version or architecture is different.
```

$ mkdir /tmp/extract
$ cd /tmp/extract
$ dpkg -x /var/cache/apt/archives/apache2.2-common_2.2.16-1ubuntu3.1_amd64.deb .

```
[*]Find the fresh files and copy them.
```

$ cd etc/apache2/sites-available/
$ ls -lgG
total 12
-rw-r--r-- 1  950 Nov 18 13:16 default
-rw-r--r-- 1 7469 Nov 18 13:16 default-ssl
$ sudo cp -p default* /etc/apache2/sites-available/

```
[*]Clean up.  Fix ownership.
```

$ cd /etc/apache2/sites-avilable/
$ sudo chown root:root default*
$ rm -rf /tmp/extract

```
[/LIST]

---

