---
title: "Ubuntu Server 64bit + Tonido"
date: 2011-06-28
forum: General Help
---

### Post by Veector on 2011-06-28
I downloaded the ```
TonidoSetup_i686.deb
``` file. I tried intalling with this command ```
sudo dpkg --force-architecture -i TonidoSetup_i686.deb
``` and this is what i get back ```
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 70504 files and directories currently installed.)
Preparing to replace tonido:i386 2.28.0.13941 (using TonidoSetup_i686.deb) ...
Unpacking replacement tonido:i386 ...
dpkg: dependency problems prevent configuration of tonido:i386:
 tonido:i386 depends on libc6 (>= 2.7-1).
 tonido:i386 depends on libfreetype6 (>= 2.3.5).
 tonido:i386 depends on libjpeg62.
 tonido:i386 depends on libpng12-0 (>= 1.2.13-4).
 tonido:i386 depends on zlib1g (>= 1:1.2.3.3.dfsg-1).
 tonido:i386 depends on libssl0.9.8 (>= 0.9.8f-1).
dpkg: error processing tonido:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tonido:i386
```What do i do to install tonido on my 64 bit Ubuntu server

---

### Post by Ozymandias_117 on 2011-06-28
Did you follow their installation instructions for 64-bit at the bottom? [http://www.tonido.com/help/Index.htm?context=60](http://www.tonido.com/help/Index.htm?context=60)

---

### Post by Veector on 2011-06-28
Yes I did

---

### Post by Ozymandias_117 on 2011-06-28
Have you tried installing the 32-bit versions of the programs it claims as dependencies?

---

### Post by Veector on 2011-06-28
How do i do that?

---

