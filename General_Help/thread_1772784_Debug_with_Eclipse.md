---
title: "Debug with Eclipse"
date: 2011-06-01
forum: General Help
---

### Post by tampe125 on 2011-06-01
hi, first of all, excuse me if this is not the correct section; i looked for a better one but i didn't find :(

ok, i've got this problem:
i'm currently using Eclipse under Windows, so when i started using Ubuntu i installed it there, too.

Eclipse under windows is working fine: no problem.

I'm using Ubuntu 11.04 and i got all the packets that i need (php5, xdeug etc etc) and i installed it. Xdebug is installed correctly, infact it shows up in my phpinfo screen.
i configured my php.ini with these values

```

extension=xdebug.so

zend_extension=/usr/lib/php5/20090626+lfs/xdebug.so

xdebug.profiler_enable= On
xdebug.remote_enable=On
xdebug.remote_host="localhost"
xdebug.remote_port=9000
xdebug.remote_handler="dbgp"
xdebug.remote_autostart=1

```when i start eclipse debug i get the new page on my browser, eclipse gets the xdebug session and when i stop i get the "debug session ended" on my browser.

so, you would say, where's the problem?
the problem is that eclipse doesn't stop on my break point!
even if i check the "break at the first line" box, eclipse seems ignoring it!

where am i wrong? can you help me?
thanks in advance!

---

### Post by tampe125 on 2011-06-03
found!

i had to remove this line

```

extension=xdebug.so

```

now everything works fine

---

