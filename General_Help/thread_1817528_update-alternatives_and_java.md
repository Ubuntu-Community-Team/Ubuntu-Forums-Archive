---
title: "update-alternatives and java"
date: 2011-08-03
forum: General Help
---

### Post by jbro on 2011-08-03
Hello,

I do Java development and need to use Sun's JDK. I have installed the sun-java6-jdk package and run 

```
sudo update-alternatives --config java
```

to select the Sun JVM as the default. However, while debugging I noticed that the OpenJDK's jdb was being used. I checked where OpenJDK alternatives are still being used with the command

```
update-alternatives --get-selections | grep -i openjdk
```

and get the following (long) list:

> appletviewer                   manual   /usr/lib/jvm/java-6-openjdk/bin/appletviewer
apt                            manual   /usr/lib/jvm/java-6-openjdk/bin/apt
extcheck                       manual   /usr/lib/jvm/java-6-openjdk/bin/extcheck
idlj                           manual   /usr/lib/jvm/java-6-openjdk/bin/idlj
jar                            manual   /usr/lib/jvm/java-6-openjdk/bin/jar
jarsigner                      manual   /usr/lib/jvm/java-6-openjdk/bin/jarsigner
javac                          manual   /usr/lib/jvm/java-6-openjdk/bin/javac
javadoc                        manual   /usr/lib/jvm/java-6-openjdk/bin/javadoc
javah                          manual   /usr/lib/jvm/java-6-openjdk/bin/javah
javap                          manual   /usr/lib/jvm/java-6-openjdk/bin/javap
javaws                         auto     /usr/lib/jvm/java-6-openjdk/jre/bin/javaws
jconsole                       manual   /usr/lib/jvm/java-6-openjdk/bin/jconsole
jdb                            manual   /usr/lib/jvm/java-6-openjdk/bin/jdb
jexec                          auto     /usr/lib/jvm/java-6-openjdk/jre/lib/jexec
jhat                           manual   /usr/lib/jvm/java-6-openjdk/bin/jhat
jinfo                          manual   /usr/lib/jvm/java-6-openjdk/bin/jinfo
jmap                           manual   /usr/lib/jvm/java-6-openjdk/bin/jmap
jps                            manual   /usr/lib/jvm/java-6-openjdk/bin/jps
jrunscript                     manual   /usr/lib/jvm/java-6-openjdk/bin/jrunscript
jsadebugd                      manual   /usr/lib/jvm/java-6-openjdk/bin/jsadebugd
jstack                         manual   /usr/lib/jvm/java-6-openjdk/bin/jstack
jstat                          manual   /usr/lib/jvm/java-6-openjdk/bin/jstat
jstatd                         manual   /usr/lib/jvm/java-6-openjdk/bin/jstatd
keytool                        auto     /usr/lib/jvm/java-6-openjdk/jre/bin/keytool
mozilla-javaplugin.so          auto     /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
native2ascii                   manual   /usr/lib/jvm/java-6-openjdk/bin/native2ascii
orbd                           auto     /usr/lib/jvm/java-6-openjdk/jre/bin/orbd
pack200                        auto     /usr/lib/jvm/java-6-openjdk/jre/bin/pack200
pluginappletviewer             auto     /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer
policytool                     manual   /usr/lib/jvm/java-6-openjdk/jre/bin/policytool
rmic                           manual   /usr/lib/jvm/java-6-openjdk/bin/rmic
rmid                           auto     /usr/lib/jvm/java-6-openjdk/jre/bin/rmid
rmiregistry                    auto     /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry
schemagen                      manual   /usr/lib/jvm/java-6-openjdk/bin/schemagen
serialver                      manual   /usr/lib/jvm/java-6-openjdk/bin/serialver
servertool                     auto     /usr/lib/jvm/java-6-openjdk/jre/bin/servertool
tnameserv                      auto     /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv
unpack200                      auto     /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200
wsgen                          manual   /usr/lib/jvm/java-6-openjdk/bin/wsgen
wsimport                       manual   /usr/lib/jvm/java-6-openjdk/bin/wsimport
xjc                            manual   /usr/lib/jvm/java-6-openjdk/bin/xjc


Is there an easy way to move all 41 of these alternatives to point to the Sun version? I can write a shell script to change them all over individually, but it seems update-alternatives should have some way to do this.

Thanks and regards.

---

### Post by Jouke S on 2011-08-03
You can check if there's such a command simply by typing man update-alternatives. This will access the manpages.
I personally don't know, sorry

---

### Post by jbro on 2011-08-03
> **Jouke S said:**
> You can check if there's such a command simply by typing man update-alternatives. This will access the manpages.
I personally don't know, sorry
Um, thank you? I know how man and update-alternatives work. Perhaps a better question is is there a link group that controls all java-related alternatives? As far as I can tell this does not exist and each alternative must be configured individually.

---

### Post by jbro on 2011-08-03
OK, I got impatient and have a workaround (see below). I would still like to know if update-alternatives has a better way of handling this.

Anyway here's a script that will change all Java-related alternatives from /usr/lib/jvm/java-6-openjdk to /usr/lib/jvm/java-6-sun:


```
#!/bin/bash

update-alternatives --get-selections | grep -i openjdk |
while read line
do
    alternative=$(echo $line | awk '{print $1}')
    path=$(echo $line | awk '{print $3}')
    newpath=$(echo $path | sed -e 's/java-6-openjdk/java-6-sun/')
    status=unchanged
    if [ -f $newpath ]
    then
	status=modified
	echo "-> update-alternatives --set $alternative $newpath"
	update-alternatives --set $alternative $newpath
    else
	echo "$alternative unchanged"
    fi
done

```

Maybe this will be of use for someone else.

Regards.

---

