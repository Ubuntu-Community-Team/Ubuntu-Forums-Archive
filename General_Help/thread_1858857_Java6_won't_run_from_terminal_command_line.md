---
title: "Java6 won't run from terminal command line"
date: 2011-10-13
forum: General Help
---

### Post by Dominicus on 2011-10-13
Hi All,
I have Ubuntu 11.04.  I've installed both Open-Java6 and Sun-Java-6.  The default option is to use the Sun java.
I'm having persistent error tying to run a myfile.java script:

```
Exception in thread "main" java.lang.NoClassDefFoundError: myfile
Caused by: java.lang.ClassNotFoundException: myfile
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
Could not find the main class: myfile.  Program will exit.
```

I set the java alternative to run the sun-6 java:

```
sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode
```

My $PATH:
```
echo $PATH
/home/javier/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/myname/Scripts
```

My $CLASSPATH:
```
echo $CLASSPATH
:/home/myname/Scripts
```

My $JAVA_HOME:
```
echo $JAVA_HOME
/usr/lib/jvm/java-6-sun
```

The "myfile.java" file I wish to run is in the "/home/myname/Scripts", but keeps erring out even if I call "java myfile" from it's own folder.  Running  "java -h" or "java -version" give me the expected output from java, but "java myfile" still fails.

What setup step am I missing to be able to invoke *.java scripts from the terminal command line?

---

### Post by gmargo on 2011-10-13
I think you have omitted the compile step using **javac**.

```

$ ls -lgG Hello.*
-rw-r--r-- 1 130 2011-10-13 10:16 Hello.java

$ cat Hello.java
import java.util.*;
public class Hello {
  public static void main(String[] args) {
    System.out.println("Hello, World");
  }
}

$ java Hello
Exception in thread "main" java.lang.NoClassDefFoundError: Hello
Caused by: java.lang.ClassNotFoundException: Hello
        at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
Could not find the main class: Hello.  Program will exit.

$ javac Hello.java

$ ls -lgG Hello.*
-rw-r--r-- 1 416 2011-10-13 10:17 Hello.class
-rw-r--r-- 1 130 2011-10-13 10:16 Hello.java

$ java Hello
Hello, World

```

---

