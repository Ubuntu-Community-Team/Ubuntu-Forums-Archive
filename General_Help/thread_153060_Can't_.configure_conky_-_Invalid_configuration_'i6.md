---
title: "Can't ./configure conky - Invalid configuration 'i686-pc-linux-oldld'"
date: 2006-03-31
forum: General Help
---

### Post by Abdi110 on 2006-03-31
Hi, I just did a fresh new install on my laptop. Before I had no problem compiling conky. Now I get this error when I run ./configure...

abdi110@reforgotten:~/downloads/conky-1.4.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... Invalid configuration 
`i686-pc-linux-oldld': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux-oldld failed

Why is it giving me this problem, while it was able to ./configure just fine before?

---

### Post by justleen on 2006-03-31
why not install it through apt?

---

### Post by Abdi110 on 2006-03-31
Um, I don't remember exactly why. I think it may have been because the ubuntu one doesn't supports battery info or something like that. All I know is the .conkyrc file from the newer build doesn't work with the ubuntu build.

---

