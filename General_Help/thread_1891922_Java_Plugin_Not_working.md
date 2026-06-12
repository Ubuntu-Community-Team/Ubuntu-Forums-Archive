---
title: "Java Plugin Not working?"
date: 2011-12-06
forum: General Help
---

### Post by boy18nj on 2011-12-06
I've tried every possible move to make my java plugin work in firefox. It proved futile.

I'm also testing java plugin if installed thru this site- [http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp)

I'm using firefox 8.

This is my current configuration-

```

rocky@ubuntu:~/.mozilla/plugins$ ls -ltr
total 18344
-rw-rw-r-- 1 rocky rocky 18782360 2011-10-31 21:56 libflashplayer.so
lrwxrwxrwx 1 rocky rocky       59 2011-12-06 19:31 IcedTeaPlugin.so -> ./usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
lrwxrwxrwx 1 rocky rocky       58 2011-12-06 19:43 libnpjp2.so -> ./home/rocky/eviware/soapUI-4.0.0/jre/lib/i386/libnpjp2.so

```Please let me know what the heck I'm missing.

---

### Post by Firezap on 2011-12-06
Just checking, did you read this?
[https://help.ubuntu.com/community/Java?action=show&redirect=JavaInstallation](https://help.ubuntu.com/community/Java?action=show&redirect=JavaInstallation)

---

### Post by boy18nj on 2011-12-06
Thanks for reply. Yes, I followed all steps, still it won't work.

---

### Post by sammiev on 2011-12-06
I use [this]("http://sites.google.com/site/easylinuxtipsproject/java") all the time. :)

---

### Post by oldtimer7777 on 2011-12-06
It is easier just to install JRE 1.6 from the PPA instead:[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/It](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/It) is about 1/5th the way down the checklist.IMO> **boy18nj said:**
> I've tried every possible move to make my java plugin work in firefox. It proved futile.
 
I'm also testing java plugin if installed thru this site- [http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp)
 
I'm using firefox 8.
 
This is my current configuration-
 
```

rocky@ubuntu:~/.mozilla/plugins$ ls -ltr
total 18344
-rw-rw-r-- 1 rocky rocky 18782360 2011-10-31 21:56 libflashplayer.so
lrwxrwxrwx 1 rocky rocky       59 2011-12-06 19:31 IcedTeaPlugin.so -> ./usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
lrwxrwxrwx 1 rocky rocky       58 2011-12-06 19:43 libnpjp2.so -> ./home/rocky/eviware/soapUI-4.0.0/jre/lib/i386/libnpjp2.so

```Please let me know what the heck I'm missing.

---

### Post by boy18nj on 2011-12-06
> **sammiev said:**
> I use [this]("http://sites.google.com/site/easylinuxtipsproject/java") all the time. :)

Worked flawlessly, don't know what the heck it has to do with OpenJDK or IcedTeaPlugin.

---

### Post by boy18nj on 2011-12-06
> **oldtimer7777 said:**
> It is easier just to install JRE 1.6 from the PPA instead:[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/It](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/It) is about 1/5th the way down the checklist.IMO

Thanks for reply.

---

### Post by sammiev on 2011-12-06
> **boy18nj said:**
> Worked flawlessly, don't know what the heck it has to do with OpenJDK or IcedTeaPlugin.

Glad I was able to help.

---

