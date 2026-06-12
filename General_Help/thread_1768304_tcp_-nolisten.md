---
title: "tcp -nolisten"
date: 2011-05-26
forum: General Help
---

### Post by lain80 on 2011-05-26
Hi,
I have upgrade my ubuntu to natty. After this upgrade the system don't accept a remote connection with xhost.
because with 10.10 version it work fine.
```

mauri@mauri-laptop:/etc/X11/xinit$ uname -a
Linux mauri-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
mauri@mauri-laptop:/etc/X11/xinit$ cat xserverrc 
#!/bin/sh
#exec /usr/bin/X -nolisten tcp "$@"
exec /usr/bin/X "$@"
mauri@mauri-laptop:/etc/gdm$ cat gdm.schemas
...
    <schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>false</default>
    </schema>
...

```what kind of check, can I do?
```

mauri@mauri-laptop:/etc/gdm$ ps -ef | grep X
root      1740  1737  3 22:37 tty7     00:01:40 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-MbZ8fi/database -nolisten tcp vt7
mauri     5261  2817  0 23:26 pts/0    00:00:00 grep --color=auto X

```thanks for any suggest

---

### Post by lain80 on 2011-05-26
Ok I've solved with this file:
```

cat /etc/gdm/custom.conf
[security]
DisallowTCP=false

```

---

