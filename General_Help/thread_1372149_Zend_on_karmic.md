---
title: "Zend on karmic"
date: 2010-01-04
forum: General Help
---

### Post by mip on 2010-01-04
Apologies if this is the incorrect place to post this question.

I've installed apache and the zend-framework using apt. I'm using the 64bit version of karmic.

Apache is running without any problems but when I activate zend (i.e. uncomment the following line in /etc/php5/apache2/conf.d/zend-framework.ini)
```
[Zend]
include_path=${include_path} ":/usr/share/php/libzend-framework-php"
```

apache refuses to start.

Anyone seen this problem?

---

### Post by mip on 2010-01-04
Looks like it's segfaulting:

```
kernel: [ 4666.057318] apache2[5486]: segfault at 8 ip 00007f75bfeb058d sp 00007fff1b77a288 error 4 in libphp5.so[7f75bfb67000+571000
```

---

### Post by mip on 2010-01-04
[http://miknight.blogspot.com/2009/08/apache-segfaults-after-enabling-zend.html](http://miknight.blogspot.com/2009/08/apache-segfaults-after-enabling-zend.html)

---

