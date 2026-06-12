---
title: "Select Best Server fail , and apache error"
date: 2009-12-07
forum: General Help
---

### Post by koni on 2009-12-07
Good %localtime%

I've got two problems : 

1)Software Source -> Select Best Server start freezing

[IMG]http://img31.imageshack.us/img31/601/screenshotan.png[/IMG]

2) Apache can't be started

```
$ -> apache2
apache2: Syntax error on line 278 of /etc/apache2/apache2.conf: Syntax error on line 17 of /etc/apache2/conf.d/mediamate: Include directory '/etc/mediamate/modules' not found
```

Line 278 of /etc/apache2/apache2.conf = Include /etc/apache2/conf.d/

Line 17 of /etc/apache2/conf.d/mediamate = Include /etc/mediamate/modules/*.conf

Mediamate :

[IMG]http://img4.imageshack.us/img4/9351/screenshotvop.th.png[/IMG]

---

