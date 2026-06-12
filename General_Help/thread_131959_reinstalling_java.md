---
title: "reinstalling java"
date: 2006-02-17
forum: General Help
---

### Post by rkakkar on 2006-02-17
```


$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

on seeing this error, i decided to install the latest java from Sun. My question is, i've created the deb package from the rpm. now if i just do dpkg -i will it upgrade java properly? or should i remove this jre1.4.2 preinstalled with ubuntu, first? if so, how can i remove this?

---

### Post by gibson on 2006-02-17
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)

automatix did a great job of upgrading my JDK and JVM

hth

---

### Post by kaamos on 2006-02-17
No need to remove the old, you just have to
```
  sudo update-alternatives --config java
```
and choose the sun jre.

---

### Post by rkakkar on 2006-02-17
[QUOTE=kaamos]No need to remove the old, you just have to
```
  sudo update-alternatives --config java
```
and choose the sun jre.[/QUOTE]
great! thanks!! :)

---

### Post by SWAT on 2006-02-17
Or if you want to use the Java from the Java site you can use [this howto. ](http://www.zwhlug.nl/content/java_how_to_install_the_sun_java_sdk_jre_1_5_0_incl_firefox_configuation) It's handy if you want to install a new version as soon as it comes out :D

---

