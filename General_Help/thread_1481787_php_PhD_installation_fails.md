---
title: "php PhD installation fails"
date: 2010-05-12
forum: General Help
---

### Post by horizons on 2010-05-12
Hello, it seems that php PhD requires sqlite 3. But the PHP Manual says sqlite3 is already included.

I'm using Ubuntu 10.04 and PHP 5.3.2

Here's what I get when I try to install PhD:

> foo@foo-laptop:~$ sudo pear install doc.php.net/phd-beta
Did not download optional dependencies: phpdocs/PhD_PHP, phpdocs/PhD_PEAR, phpdocs/PhD_IDE, use --alldeps to download automatically
phpdocs/PhD requires PHP extension "sqlite3"
phpdocs/PhD can optionally use package "phpdocs/PhD_PHP"
phpdocs/PhD can optionally use package "phpdocs/PhD_PEAR"
phpdocs/PhD can optionally use package "phpdocs/PhD_IDE"
phpdocs/PhD can optionally use PHP extension "haru"
phpdocs/PhD_Generic requires package "phpdocs/PhD" (version >= 0.9.0)
phpdocs/PhD_Generic can optionally use PHP extension "haru"
No valid packages found
install failed

I tried to install sqlite 3, but synaptic is complaining about dependencies that cannot be found. dll hell? lol

php5-sqlite3:
 Depends: phpapi-20060613+lfs

This package isn't even in the Ubuntu 10.04 repository (the sqlite3 for php, although the sqlite3 for c is in there)

Does anyone know where I'm going wrong?
Cheers

---

