---
title: "Install latest deskbar applet..."
date: 2006-05-26
forum: General Help
---

### Post by joelomar on 2006-05-26
I tried installing deskbar on Ubuntu Breezy 5.10.  I successfully installed from the Universe repositories, but the version available there is an old one.  I downloaded the tarball but I can't install it.  It says that it needs a compiler or something:

checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I really want to try this app out.  Can anyone shed any light??

---

### Post by bruce89 on 2006-05-26
You would have to install a load of packages, the main one being build-essential.

---

### Post by joelomar on 2006-05-26
apt-get build-essential?  will try.

---

### Post by bruce89 on 2006-05-26
Also ```
apt-get build-dep deskbar-applet
```to get the build dependancies.

---

### Post by joelomar on 2006-05-26
That helped some, now I get a Perl Parser error, thus:
XML::Parser perl module is required for intltool

---

