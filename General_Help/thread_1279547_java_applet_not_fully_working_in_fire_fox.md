---
title: "java applet not fully working in fire fox"
date: 2009-09-30
forum: General Help
---

### Post by rhythmiccycle on 2009-09-30
i trying to use this page:
[http://maliszesky.dyndns.org/Classes/Geo/javaExample.php](http://maliszesky.dyndns.org/Classes/Geo/javaExample.php)

the 3 circles are supposed to be dragable.
but they are not on my laptop running ubuntu 9

i can run it with fire fox, on my other pc at it works fine.
i also tested on Internet expoler, on other computers and it works

is there a setting, or do I need another plugin??

please help

---

### Post by boblemur on 2009-10-01
hey,

first what version of the java plugin are you running?

run:
```
dpkg -l | grep sun-java.-plugin
```

and it will show you. i suggest you try install:

```
sudo aptitude install sun-java6-plugin
```

as that website works for me using that package. good luck :)

---

### Post by rhythmiccycle on 2009-10-01
this is what i got:

```

$ dpkg -l | grep sun-java.-plugin
ii  sun-java6-plugin                           6-16-0ubuntu1.9.04                        The Java(TM) Plug-in, Java SE 6

```

i think that means i already have sun-java6-plugin package.

the problem might be with firefox.

any suggestions?

---

### Post by boblemur on 2009-10-01
right ok, then your next step is to try download the applet by going to the link (in firefox) and then going save page as, and it will save the html page and a folder called javaExample.php_files inside you will find a file called:

```
triangleApp13php.jar
```

right click and go open with "Sun Java 6 Runtime" and try see if you can drag it, this will show you if it is your JRE or if it is firefox, then we can narrow our search further :)

---

### Post by rhythmiccycle on 2009-10-01
> **boblemur said:**
> 

```
triangleApp13php.jar
```

right click and go open with "Sun Java 6 Runtime" and try see if you can drag it, this will show you if it is your JRE or if it is firefox,

i did that, and it is not working. so it seems firefox is not the problem.

also, when i opened it in "Sun Java 6 Runtime" the window wouldn't close, i had to force quit it. 

it seem like the applet is freezing up some how. because i can see the applet, but i cannot interact with it.

---

### Post by boblemur on 2009-10-01
does the submit button work at all?

first try in terminal (assuming you saved the folder onto your desktop):
```
~/Desktop/javaExample.php_files
java -jar triangleApp13php_002.jar

```

let me know if you get any error messages or any more information.

also try double clicking the node at the corner of the triangle then try move it. if this dosent work try the following in terminal:
```
sudo renice -10 -p `ps aux | grep triangle | grep -v grep | awk '{print $2}'`
```

that code will renice (change the process priority) to the task that is running the triangle application so that it has "Very High Priority" this will rule out any lag non responsiveness due to processing. (the applet must be open, using the commands above).

again, good luck :)

---

### Post by pothikan on 2009-10-13
Hey.. try this out ..

1. Goto synaptic package manager
2. **Uninstall** the "**sun-java6(or 5)-plugin**" you already have
2. **Install** the "**icedtea6-plugin**" (supports java applets to execute in web browser)

Hope this will resolve your issue.

---

### Post by rhythmiccycle on 2009-10-15
> **boblemur said:**
> does the submit button work at all?



no, I can't even move the circles (A B C)

i tried the code and got:
```

:~$ cd Desktop/
:~/Desktop$ cd javaExample.php_files/
:~/Desktop/javaExample.php_files$ java -jar triangleApp13php_002.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
	at java.awt.Component.<clinit>(Component.java:568)
Could not find the main class: triangleApp13php. Program will exit.



```

---

### Post by rhythmiccycle on 2009-10-15
> **boblemur said:**
> 

also try double clicking the node at the corner of the triangle then try move it. if this dosent work try the following in terminal:
```
sudo renice -10 -p `ps aux | grep triangle | grep -v grep | awk '{print $2}'`
```

that code will renice (change the process priority) to the task that is running the triangle application so that it has "Very High Priority" this will rule out any lag non responsiveness due to processing. (the applet must be open, using the commands above).




clicking the node does not work at all. 

I also did the renice code while the jar file was opened in java runtime environment, but there was no effect. nothing workied, and I still had to force quit to close the window.

---

### Post by boblemur on 2009-10-15
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```

shows that its trying to load the open source java try to run the sun-java version:

```

cd ~/Desktop/javaExample.php_files
/usr/lib/jvm/java-6-sun/bin/java -jar triangleApp13php_002.jar

```

if that works:

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

then the above will make it perminant

---

### Post by rhythmiccycle on 2009-10-15
> **boblemur said:**
> 

```

cd ~/Desktop/javaExample.php_files
/usr/lib/jvm/java-6-sun/bin/java -jar triangleApp13php_002.jar

```

if that works:



it didn't work, its still opened the same way.

---

### Post by boblemur on 2009-10-15
Try the second half of my post none the less, and if that dosen't work im afraid im out of ideas sorry

---

### Post by rhythmiccycle on 2009-10-16
this is what i did:
```

:~$ sudo update-java-alternatives -l

java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk

java-6-sun 63 /usr/lib/jvm/java-6-sun



:~$ sudo update-java-alternatives -s java-6-sun

No alternatives for appletviewer.

No alternatives for apt.

No alternatives for extcheck.

No alternatives for HtmlConverter.

No alternatives for idlj.

No alternatives for jar.

No alternatives for jarsigner.

No alternatives for javac.

No alternatives for javadoc.

No alternatives for javah.

No alternatives for javap.

No alternatives for java-rmi.cgi.

No alternatives for jconsole.

No alternatives for jdb.

No alternatives for jhat.

No alternatives for jinfo.

No alternatives for jmap.

No alternatives for jps.

No alternatives for jrunscript.

No alternatives for jsadebugd.

No alternatives for jstack.

No alternatives for jstat.

No alternatives for jstatd.

No alternatives for native2ascii.

No alternatives for pluginappletviewer.

No alternatives for rmic.

No alternatives for schemagen.

No alternatives for serialver.

No alternatives for wsgen.

No alternatives for wsimport.

No alternatives for xjc.

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport

update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc

Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.

Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'firefox-javaplugin.so'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'iceape-javaplugin.so'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'iceweasel-javaplugin.so'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'midbrowser-javaplugin.so'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'mozilla-javaplugin.so'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'xulrunner-1.9-javaplugin.so'.

Using '/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so' to provide 'xulrunner-javaplugin.so'.


:~$ java -version

java version "1.6.0_16"

Java(TM) SE Runtime Environment (build 1.6.0_16-b01)

Java HotSpot(TM) Client VM (build 14.2-b01, mixed mode, sharing)


:~$ cd ~/Desktop/javaExample.php_files

:~/Desktop/javaExample.php_files$ java -jar triangleApp13php_002.jar


```

this time the jar file opened without any errors (in the terminal), but the applet still is not working. Same problem, it shows up, but I cannot interact with it, and I need to force quit to close it.

---

### Post by rhythmiccycle on 2009-10-16
> **boblemur said:**
> Try the second half of my post none the less, and if that dosen't work im afraid im out of ideas sorry

thanks anyway, I hope someone else know how to fix this.

Or do you think it could be a hardware problem?

---

