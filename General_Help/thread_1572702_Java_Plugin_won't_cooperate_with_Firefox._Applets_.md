---
title: "Java Plugin won't cooperate with Firefox. Applets won't load."
date: 2010-09-11
forum: General Help
---

### Post by anthony62490 on 2010-09-11
Last time I checked, Java was a platform-independent language. Unless that's changed since the last time I checked, I probably have a problem with my Java plugin.

I tried to play MineCraft yesterday, but it wouldn't load all the way. It would get right to the point of launching the game and then give a black screen. At this point, I had the following packages (note that I am just pasting all the packages that even mention the word Java):

```
ca-certificates-java
gcj-4.4-jre
gcj-4.4-jre-headless
gcj-jre
gcj-jre-headless
icedtea6-plugin
java-common
libaccess-bridge-java
libaccess-bridge-java-ini
libclucene0ldbl
libgcj10
libswt-gtk-3.5-java
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
sun-java6-bin
sun-java6-jdk
sun-java6-jre
tzdata-java
```

I was told that the OpenJDK and IcedTea packages were conflicting with the Sun packages, so I removed them.

**sudo apt-get remove icedtea6-plugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib**

I also checked a guide to installing Java to see if I missed any steps. I apparently skipped one. I installed **sun-java6-fonts**. It didn't help.

At this point, MineCraft (as well as any other Java applet) won't load at all. Not even the black frame is loaded.

-------------------------------------------------
-------------------------------------------------

Fast forward to today. I currently have the following Java-related packages:

```
ca-certificates-java
gcj-4.4-jre
gcj-4.4-jre-headless
gcj-jre
gcj-jre-headless
java-common
libclucene0ldbl
libgcj10
libswt-gtk-3.5-java
sun-java6-bin
sun-java6-fonts
sun-java6-jdk
sun-java6-jre
sun-java6-plugin
```

**Java -version** gives me this:
```
anthony@anthony-desktop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

**dpkg-reconfigure sun-java6-jre** gives me this:
```
anthony@anthony-desktop:~$ sudo dpkg-reconfigure sun-java6-jre 
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
```

Typing **about:plugins** into Firefox shows me my Flash plugin, my VLC plugin, and my QuickTime plugin. It says nothing about Java.

I am running **9.10 Karmic** and using **Firefox v.3.6.9**


Okay, that's all the information I can think of right now. Any help at all will be appreciated.

---

### Post by anthony62490 on 2010-09-11
bump

---

### Post by anthony62490 on 2010-09-11
nobody?

---

