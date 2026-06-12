---
title: "LibreOffice doesn't start"
date: 2011-10-21
forum: General Help
---

### Post by sbardascione on 2011-10-21
Hello everybody, 
i installed libreoffice, when i try to start it shows only splash screen and then nothing.
I tried to start it from terminal but it gives no error.
Ideas?
Thank you.

P.S. the problem comes from upgrade from 11.04 to 11.10

---

### Post by 2F4U on 2011-10-22
So it says nothing when started out of a terminal? Did you also look into the system log files?

---

### Post by sbardascione on 2011-10-23
It says nothing from terminal. Dmesg says :

soffice.bin[2509]: segfault at 0 ip 00007f7e6bd6faba sp 00007fff0b746b90 error 4 in libsofficeapp.so[7f7e6bd3f000+6a000]

---

### Post by sbardascione on 2011-10-24
up

---

### Post by mikejonesey on 2011-10-24
try setting the JAVA_HOME env var to another jdk/jre...
```
export JAVA_HOME=/where your new jdk is (try jdk 1.6.0_22 or above)
```
then run libre office from same terminal and post output

---

### Post by sbardascione on 2011-10-24
Did it, but nothing changes.

```
 export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.26
```

libreoffice still gives nothing.

---

### Post by mikejonesey on 2011-10-24
java libreoffice 2> mytmp.log

then use Ctrl+D/Ctrl+C, java will print a stacktrace to the log or 2>&1 to stdout... see if any clues in there...

---

### Post by sbardascione on 2011-10-24
java can't find the class "libreoffice"
```

carmelo@carmelo-laptop:~$ java libreoffice 2>&1
Exception in thread "main" java.lang.NoClassDefFoundError: libreoffice
Caused by: java.lang.ClassNotFoundException: libreoffice
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
Could not find the main class: libreoffice.  Program will exit.


```

---

### Post by sbardascione on 2011-10-24
Just renamed the folder ~/.libreoffice and works... don't know why... however thank you!:)

---

