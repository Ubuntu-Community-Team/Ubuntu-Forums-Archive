---
title: "Natty Java/Minecraft Server problems"
date: 2011-08-22
forum: General Help
---

### Post by teasplurt on 2011-08-22
Hi guys,
I'm trying to run a minecraft server on my 64-bit, 11.04 Natty Narwhal machine, but the server *.jar is returning some odd errors which I did not run into previously.
I've tried both of the OpenJDK and Sun Java runtime environments, and received the same error both times.
I execute the following command in my server directory after chmod'ing the executable:
[INDENT]sudo java ./minecraft-server.jar[/INDENT]
...and receive the following output:
[INDENT]Exception in thread "main" java.lang.NoClassDefFoundError: //minecraft-server/jar
Caused by: java.lang.ClassNotFoundException: ..minecraft-server.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: ./minecraft-server.jar. Program will exit.[/INDENT]
I'm not sure what all of this means; I'm not too familiar with Java.  I have another machine running 10.10 which runs this just fine...however, that computer is also 32-bit, so I'm not sure which poses this problem.

---

### Post by Dark Slipstream on 2011-08-22
As long as you have enabled running the file as an executable then just execute it like so:

```
./minecraft-server.jar
```

If you plan on running it using the java command, you need to specify the memory parameters, like so:

```
java -Xms1023M -Xmx1024M -jar minecraft-server.jar
```

---

