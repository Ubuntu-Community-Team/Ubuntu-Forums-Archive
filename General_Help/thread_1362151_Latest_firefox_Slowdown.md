---
title: "Latest firefox Slowdown"
date: 2009-12-22
forum: General Help
---

### Post by ethoxyethaan on 2009-12-22
the lastest firefox release is slower compared to the old builds, 

when i check the build options it says:

```
--build=x86_64-linux-gnu --prefix=/usr '--includedir=/usr/include' '--mandir=/usr/share/man' '--infodir=/usr/share/info' --sysconfdir=/etc --localstatedir=/var '--libexecdir=/usr/lib/xulrunner-1.9.1' --disable-maintainer-mode --disable-dependency-tracking --srcdir=. --enable-tests --enable-mochitest --enable-system-cairo --enable-system-sqlite --with-system-nspr --with-system-nss --enable-system-hunspell --enable-application=xulrunner --enable-extensions=default,python --with-default-mozilla-five-home=/usr/lib/xulrunner-1.9.1.6 --enable-safe-browsing --enable-startup-notification --with-user-appdir=.mozilla --without-system-jpeg --with-system-zlib=/usr --with-system-bz2=/usr --disable-javaxpcom --disable-crashreporter --disable-elf-dynstr-gc --disable-installer --disable-strip --disable-strip-libs --disable-install-strip --disable-updater --enable-optimize --with-distribution-id=com.ubuntu 
```
gcc: ```
-Wall -W -Wno-unused -Wpointer-arith -Wcast-align -W -Wno-long-long -pedantic -g -fno-strict-aliasing -pthread -pipe -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions
```

currently Os is being used but i don't understand why firefox is still slower than the previous versions. 

last time i build Firefox it took me a good Hour of compiling so i hope they will use the old build options soon :(.

---

### Post by lovinglinux on 2009-12-23
Did you compared both builds with a clean profile? If not, than some changes in the Firefox profile might be causing the difference. For example a bookmark database full of junk.

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

