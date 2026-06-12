---
title: "help with conky"
date: 2006-06-14
forum: General Help
---

### Post by souteneur3190 on 2006-06-14
I was trying to install conky and this happend

malubankudi@ubuntu:~$ cd /home/malubankudi/Desktop/conky-1.4.2
malubankudi@ubuntu:~/Desktop/conky-1.4.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... Invalid configuration `i686-pc-linux-oldld': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux-oldld failed
malubankudi@ubuntu:~/Desktop/conky-1.4.2$

wut can i do?

---

### Post by Ramses de Norre on 2006-06-14
sudo aptitude install conky?

---

### Post by taurus on 2006-06-14
Or
```

sudo apt-get install build-essential

```

---

