---
title: "Eclipse help?"
date: 2011-04-04
forum: General Help
---

### Post by 13thAngel on 2011-04-04
Trying to install eclipse classic 3.6.2. It installs just fine however it will not run. Keep getting this error message....

> 
JVM terminated. Exit code=13
/usr/bin/java
-Xms40m
-Xmx384m
-XX:MaxPermSize=256m
-jar /home/dusty/eclipse//plugins/org.eclipse.equinox.launcher_1.1.1.R36x_v20101122_1400.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/dusty/eclipse/eclipse
-name Eclipse
--launcher.library /home/dusty/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.2.R36x_v20101019_1345/eclipse_1310.so
-startup /home/dusty/eclipse//plugins/org.eclipse.equinox.launcher_1.1.1.R36x_v20101122_1400.jar
-exitdata 6c8011
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx384m
-XX:MaxPermSize=256m
-jar /home/dusty/eclipse//plugins/org.eclipse.equinox.launcher_1.1.1.R36x_v20101122_1400.jar I have both java-1.5.0 and java6 installed. When i try to run "sudo update-java-alternatives -s java-1.5.0-sun" i get

> 
update-alternatives: error: no alternatives for firefox-javaplugin.so.
update-alternatives: error: no alternatives for iceape-javaplugin.so.
update-alternatives: error: no alternatives for iceweasel-javaplugin.so.
update-alternatives: error: no alternatives for midbrowser-javaplugin.so.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-javaplugin.so.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
Not sure if theyre connected but i figured they might be....

---

### Post by 13thAngel on 2011-04-04
Bump..... anyone?

---

### Post by Azdour on 2011-04-04
Hi,

I do not know the answer but have you seen this thread:

[http://ubuntuforums.org/showthread.php?t=621493](http://ubuntuforums.org/showthread.php?t=621493)

I know its old but maybe it will point you in the right direction?

---

### Post by 13thAngel on 2011-04-04
I had saw that one before, tried it but no dice. I am on a 32-bit system anyways.

Thanks though.

---

### Post by Azdour on 2011-04-06
Hi,

To switch Java I usually use:

```
sudo update-alternatives --config java
```

That way it gives me a list of the Java's that are actually installed. I'm guessing that:

```
sudo update-java-alternatives -s java-1.5.0-sun
```

Is a short-cut to specifying the Java you want, is the java-1.5.0-sun correct? 

Saying that, Eclipse 3.6.2 should run with both sun java 1.5 and 1.6

The other thing you may want to try is edit the eclipse.ini file and tell it which jvm to use, e.g:

```
-vm
/usr/lib/jvm/java-6-sun/bin/java
```

---

