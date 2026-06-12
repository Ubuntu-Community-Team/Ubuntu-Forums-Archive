---
title: "Firefox 4.0 und Java 1.6.0_21 plugin"
date: 2010-08-28
forum: General Help
---

### Post by DrStrom on 2010-08-28
Hallo,

ich bekomme es einfach nicht hin das Java plugin 1.6.0_21 in Firefox 4.0 zu installieren. ich hatte vorher das Icedtea Plugin deinstalliert und dann mit ln -s versucht das plugin zu installieren.

meine Frage : kann es sein das ich bei der deinstallation etwas falsch gemacht habe ?
wie bekomme ich ein Plugin freien Firefox ? So das nichts stören könnte.

---

### Post by lovinglinux on 2010-08-28
Hello. 

Please keep in mind this forum only allows English posts.

Firefox 4 is still at Beta stage, so it is normal to have such problems. Nevertheless, I'm running Firefox 4.0b4 with IcedTea and it is working properly.

To install it, run the following command on a terminal:

```
sudo apt-get install icedtea6-plugin
```

Then restart your browser, then type **about[noparse]:[/noparse]plugins** in Firefox address bar and check if IcedTea is recognized and visit the [java test page]("ttp://www.java.com/en/download/help/testvm.xml").

---

