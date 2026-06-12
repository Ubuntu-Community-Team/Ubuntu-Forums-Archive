---
title: "php5 in lib not bin"
date: 2011-06-06
forum: General Help
---

### Post by berryboy on 2011-06-06
hello :) i have installed php5 
apt-get install php5
installed fine but when i got to a php program its looks for it in 
line 90: /usr/bin/php: No such file or directory

whereis:
~# whereis php5
php5: /usr/bin/php5 /etc/php5 /usr/lib/php5 /usr/share/php5
 iv added a symlink to bin as u can see above but thats no good as the php is looking for it in /usr/bin/php

how can i get /usr/bin/php. drag php5 folder in there and rename it? i dont want to mess anything up !!

---

### Post by Joe of loath on 2011-06-06
symlink ./php5 to ./php and try that.

---

### Post by Dave_L on 2011-06-06
On my system, /usr/bin/php is a symbolic link to /etc/alternatives/php, and /etc/alternatives/php is a symbolic link to /usr/bin/php5:

```
$ file /usr/bin/php
/usr/bin/php: symbolic link to `/etc/alternatives/php'

$ ll /usr/bin/php
lrwxrwxrwx 1 root root 21 2011-03-26 12:25 /usr/bin/php -> /etc/alternatives/php*

$ file /etc/alternatives/php
/etc/alternatives/php: symbolic link to `/usr/bin/php5'

$ ll /etc/alternatives/php
lrwxrwxrwx 1 root root 13 2011-03-26 12:25 /etc/alternatives/php -> /usr/bin/php5*

$ file /usr/bin/php5
/usr/bin/php5: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

$ ll /usr/bin/php5
-rwxr-xr-x 1 root root 7467156 2011-05-02 21:00 /usr/bin/php5*
```

---

### Post by berryboy on 2011-06-06
i did

sudo apt-get install php5-cli

sudo apt-get install php5-cgi

all is working thank you very much for your responces though!! :)

---

