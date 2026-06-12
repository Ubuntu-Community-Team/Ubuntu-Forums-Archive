---
title: "file command dose not work !"
date: 2011-11-08
forum: General Help
---

### Post by zaichou on 2011-11-08
hi,all
file command does not work on my ubuntu 10.04.

the report as :

/etc/magic, 4: Warning using regular magic file `/usr/share/misc/magic'
/usr/share/misc/magic, 320: Warning offset `!:mime      video/x-sgi-movie' invalid
/usr/share/misc/magic, 320: Warning type `!:mime        video/x-sgi-movie' invalid
/usr/share/misc/magic, 322: Warning offset `!:mime      video/quicktime' invalid
/usr/share/misc/magic, 322: Warning type `!:mime        video/quicktime' invalid
/usr/share/misc/magic, 328: Warning offset `!:mime      video/quicktime' invalid
/usr/share/misc/magic, 328: Warning type `!:mime        video/quicktime' invalid
/usr/share/misc/magic, 336: Warning offset `!:mime      image/x-quicktime' invalid
/usr/share/misc/magic, 336: Warning type `!:mime        image/x-quicktime' invalid
/usr/share/misc/magic, 340: Warning offset `!:mime      application/x-quicktime-player' invalid
/usr/share/misc/magic, 340: Warning type `!:mime        application/x-quicktime-player' invalid
/usr/share/misc/magic, 342: Warning offset `!:mime      image/jp2' invalid
/usr/share/misc/magic, 342: Warning type `!:mime        image/jp2' invalid
/usr/share/misc/magic, 345: Warning offset `!:mime      video/mp4' invalid
..................................
/usr/share/misc/magic, 15203: Warning type `!:mime      application/x-ichitaro6' invalid
/usr/share/misc/magic, 15208: Warning offset `!:mime    application/x-freemind' invalid
/usr/share/misc/magic, 15208: Warning type `!:mime      application/x-freemind' invalid
/usr/share/misc/magic, 15214: Warning offset `!:mime    application/x-scribus' invalid
/usr/share/misc/magic, 15214: Warning type `!:mime      application/x-scribus' invalid
/usr/share/misc/magic, 15391: Warning offset `!:mime    image/x-xcursor' invalid
/usr/share/misc/magic, 15391: Warning type `!:mime      image/x-xcursor' invalid
file: File 4.23 supports only 4 version magic files. `/usr/share/misc/magic.mgc' is version 7

is there any ideas?
thanks!!

---

### Post by Lampi on 2011-11-08
10.04? that's Lucid Lynx -> how come your version of "file" is 4.23 ?!?

Here's what it *should* be if you don't tamper with the system:

```
file --version
file-5.03
magic file from /etc/magic:/usr/share/misc/magic

apt-cache policy file
file:
  installed: 5.03-5ubuntu1
  candidate: 5.03-5ubuntu1
  Versions:
 *** 5.03-5ubuntu1 0
        500 [http://xx.archive.ubuntu.com/ubuntu/](http://xx.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by zaichou on 2011-11-09
thanks,Lampi.
i've found a thread to solve my problem .
[http://forums.gentoo.org/viewtopic-t-840585.html](http://forums.gentoo.org/viewtopic-t-840585.html)
 
> [COLOR=#000000]I finally tracked it down. I'm running Zend Server CE on my laptop to access the Zend debugger. I updated to the 5.0.2 release and unlike the previous 5.0.0 version, it dropped a config file in /etc/ld.so.conf.d which added the Zend Server libraries in /usr/local/zend/lib to my LD_LIBRARY_PATH. Needless to say, this caused all sorts of trouble. I removed the config file, ran ldconfig and all seems to be back to normal. [/COLOR]

---

