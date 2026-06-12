---
title: "OpenVPN-ALS (Adito) on Lucid - Service Starts then Dies &quot;Exception in thread &quot;main&quot;&quot;"
date: 2010-05-21
forum: General Help
---

### Post by charon79m on 2010-05-21
Google tells me this is an error in java not knowing its classpath.  IANAP, and could use some help in resolving this.

I've followed the instructions available at various sites, and the installation went fine.

When I start the service I get the following in the wrapper.log:

```
root@twin:/etc# service adito console
Running Adito...
wrapper  | --> Wrapper Started as Console
wrapper  | Launching a JVM...
jvm 1    | Exception in thread "main" java.lang.NoClassDefFoundError: Main
jvm 1    | Caused by: java.lang.ClassNotFoundException: Main
jvm 1    | 	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
jvm 1    | 	at java.security.AccessController.doPrivileged(Native Method)
jvm 1    | 	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
jvm 1    | 	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
jvm 1    | 	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
jvm 1    | 	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
jvm 1    | Could not find the main class: Main.  Program will exit.
...
... PREVIOUS LINES REPEAT 5 TIMES ...
...
wrapper  | JVM exited while loading the application.
wrapper  | There were 5 failed launches in a row, each lasting less than 300 seconds.  Giving up.
wrapper  |   There may be a configuration problem: please check the logs.
wrapper  | <-- Wrapper Stopped
```

Any suggestions would be greatly appreciated.

M. Knisely

---

### Post by BiL0 on 2010-09-22
I have the exact same problem and I tried with several different version.
running the console it shows the same error.
there is another thread but no answer 
[http://guide.ubuntuforums.org/showthread.php?p=9860642](http://guide.ubuntuforums.org/showthread.php?p=9860642)

---

### Post by BiL0 on 2010-09-22
Hello
not sure what's wrong but try the following, it worked for me

after you finish the install, instead of starting from /etc/init.d/
try to start this from the adito installer
go in and run 
"ant start"
that should start and then check that your 443 port is available 
not sure what's the difference there but it works for me

hope it helps

B

---

### Post by paped on 2011-02-21
I have had the same problem on 10.04.1 where the service starts then 20 seconds later it stops... I think I have a fix or at least it has worked for me....

1) (Not sure if this is needed or not but I did it so worth a mention) Go to ~/Adito Dir/conf and type "nano wrapper.conf" and comment out all the entries for the Windows 2000/XP etc service at the bottom of the file. While in here to fix the invalid login credentials problem also find the line of : "#wrapper.java.additional.2=-Dfile.encoding=UTF-8"    - Which is about half way down and remove the #. Then save this file.

2) (I think this is the thing that may have fixed it) type "nano webserver.properties" (in the same dir as above) check the file and if you see any entries split by "\!\!" remove one of them so the line becomes "item1\!item2\!item3, hence there should only be one \! not 2 of them. Save this file.

Start Adito and this time it should work....

Note: I think there is a bug on the System Configuration page somewhere and when it writes the webserver.properties file it's parsing out the extra "\!", hence if you change anything in this section in the future this issue may return and you will need to do the above editing again....

Hope this help.....

---

