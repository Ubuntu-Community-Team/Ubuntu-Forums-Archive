---
title: "Software Center all installs stop at Applying Changes 90%"
date: 2011-04-04
forum: General Help
---

### Post by OGWacco on 2011-04-04
I installed Iced tea to run java stuff today from Software Center.
The Iced tea installed and works like it should but i get a error message when applying changes is at 90%. 
The same error comes with deletes and other downloads too. 
Here is the message:

```
InstallArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
Selecting previously deselected package openjdk-6-jre-lib. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 160022 files and directories currently installed.) 
Unpacking openjdk-6-jre-lib (from .../openjdk-6-jre-lib_6b20-1.9.7-0ubuntu1~10.04.1_all.deb) ... 
Selecting previously deselected package openjdk-6-jre-headless. 
Unpacking openjdk-6-jre-headless (from .../openjdk-6-jre-headless_6b20-1.9.7-0ubuntu1~10.04.1_amd64.deb) ... 
Selecting previously deselected package ca-certificates-java. 
Unpacking ca-certificates-java (from .../ca-certificates-java_20100406ubuntu1_all.deb) ... 
Selecting previously deselected package libaccess-bridge-java-jni. 
Unpacking libaccess-bridge-java-jni (from .../libaccess-bridge-java-jni_1.26.2-3_amd64.deb) ... 
Selecting previously deselected package openjdk-6-jre. 
Unpacking openjdk-6-jre (from .../openjdk-6-jre_6b20-1.9.7-0ubuntu1~10.04.1_amd64.deb) ... 
Selecting previously deselected package libaccess-bridge-java. 
Unpacking libaccess-bridge-java (from .../libaccess-bridge-java_1.26.2-3_all.deb) ... 
Selecting previously deselected package icedtea-6-jre-cacao. 
Unpacking icedtea-6-jre-cacao (from .../icedtea-6-jre-cacao_6b20-1.9.7-0ubuntu1~10.04.1_amd64.deb) ... 
Selecting previously deselected package icedtea6-plugin. 
Unpacking icedtea6-plugin (from .../icedtea6-plugin_6b20-1.9.7-0ubuntu1~10.04.1_amd64.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.fi_FI.UTF8.cache... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-support ... 
Setting up man-db (2.5.7-2ubuntu1) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up openjdk-6-jre-headless (6b20-1.9.7-0ubuntu1~10.04.1) ... 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/java to provide /usr/bin/java (java) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode. 
 
Setting up openjdk-6-jre-lib (6b20-1.9.7-0ubuntu1~10.04.1) ... 
 
Setting up libaccess-bridge-java (1.26.2-3) ... 
Setting up libaccess-bridge-java-jni (1.26.2-3) ... 
 
Setting up icedtea-6-jre-cacao (6b20-1.9.7-0ubuntu1~10.04.1) ... 
Setting up ca-certificates-java (20100406ubuntu1) ... 
 
Setting up openjdk-6-jre (6b20-1.9.7-0ubuntu1~10.04.1) ... 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer to provide /usr/bin/pluginappletviewer (pluginappletviewer) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode. 
 
Setting up icedtea6-plugin (6b20-1.9.7-0ubuntu1~10.04.1) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 man-db 
Setting up man-db (2.5.7-2ubuntu1) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1
```

---

### Post by wolfen69 on 2011-04-04
Are you running synaptic or the update manager at the same time?

---

