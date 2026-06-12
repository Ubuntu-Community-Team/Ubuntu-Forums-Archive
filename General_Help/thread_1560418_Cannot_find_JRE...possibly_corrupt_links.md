---
title: "Cannot find JRE...possibly corrupt links?"
date: 2010-08-24
forum: General Help
---

### Post by Zentraleinheite on 2010-08-24
Hi everyone,

My java is installed at 

/usr/lib/jvm/java-6-sun-1.6.0.15/bin


output: 
```

user@box:/usr/lib/jvm/java-6-sun-1.6.0.15/jre/bin$ ./java -version

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)
```

But running it elsewhere fails with
cannot find JRE errors (& libjava.so)

other output:
```

user@box:/$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/bin/

user@box:/$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer:/usr/lib/jvm/java-6-sun-1.6.0.15/bin/java

```

---

### Post by Brandon Williams on 2010-08-26
First, how did you install java? Did you install the package from the partner repo? If you do, then all the necessary symlinks should be set up for you so that java just works. If not, then completing the setup can be a bit of a pain.

If you did install from the partner repo, then I suggest that you reinstall in the hope that the symlinks get fixed by the reinstall of sun-java6-jre. If you use the package from the partner repo, then you won't need to modify your PATH or JAVA_HOME, and you'll get automatic security updates, etc.

If you didn't install from the partner repo and you can't for some reason, then I think the settings you want are:
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.15/
PATH=$PATH:$JAVA_HOME/bin
```

---

