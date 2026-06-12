---
title: "Error when install karamba"
date: 2006-06-12
forum: General Help
---

### Post by mzainal on 2006-06-12
This error came out when i install karamba:

root@ubuntu:/home/banie/My Downloads/superkaramba# ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
/bin/sh: /home/banie/My: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

How to fix it?
Thank you.

---

### Post by aschaetter on 2007-11-18
open a terminal window and type "sudo apt-get install kde-config"

---

