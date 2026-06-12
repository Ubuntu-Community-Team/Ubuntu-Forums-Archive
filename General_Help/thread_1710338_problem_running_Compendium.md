---
title: "problem running Compendium"
date: 2011-03-19
forum: General Help
---

### Post by paparon on 2011-03-19
I'm new to Ubuntu; a couple of weeks. I'm using Ubuntu 10.10
I'm trying to install and run Compendium.
The instructions were to download & unpack the tar.gz file, go to that directory and run compendium.sh. They also said to use Sun Java JRE rather than OpenJDK Java.

I had OpenJDK installed so I uninstalled it. I don't remember installing JRE but I have both JRE 6 architecture independent and JRE 6 architecture dependent installed.

I unpacked the Compendium tar.gz in /user/bin, gave my group permission to run as a program and entered ./Compendium.sh in the terminal.

I got this message:

Exception in thread "main" java.lang.NoClassDefFoundError: com/compendium/ProjectCompendium
Caused by: java.lang.ClassNotFoundException: com.compendium.ProjectCompendium
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: com.compendium.ProjectCompendium. Program will exit.

I don't know what that means. Can someone help.

Thanks.

---

### Post by lykeion on 2011-03-20
First of all a tip: 
Enclose code output using the # button, it's much easier to read it that way.

About your problem: 
You'll probably have to manually edit the start script Compendium.sh, but it's hard to say just how exactly unless you

1) Provide links for where you downloaded Compendium
[INDENT]or[/INDENT]
2) Copy and paste the the contents of the start script here

---

### Post by paparon on 2011-03-20
Thanks, lykeion, for responding.

I downloaded the software from [http://compendium.open.ac.uk/openlearn/download-linux.html](http://compendium.open.ac.uk/openlearn/download-linux.html)

Here is the contents of Compendium.sh: 

java -Xmx512m -cp .:System/lib/compendiumcore.jar:System/lib/compendium.jar:System/lib/AppleJavaExtensions.jar:System/lib/jhall.jar:System/lib/kunststoff.jar:System/lib/jabberbeans.jar:System/lib/mysql-connector-java-5.1.6-bin.jar:System/lib/derby.jar:System/lib/triplestore.jar:System/lib/xml.jar:System/lib/jmf-all.jar:System/lib/crew.jar:System/lib/fobs4jmf.jar com.compendium.ProjectCompendium %1 %2 %3 %4 %5 %6 %7 %8 %9

By enclosing the code output using the # button, I assume you mean to put a # before and after the output. I'll try it.

Thanks again,

---

### Post by lykeion on 2011-03-20
> **paparon said:**
> By enclosing the code output using the # button, I assume you mean to put a # before and after the output. I'll try it.
I did not. When you're editing your post you'll see a menu with icons above. To enclose something in code tags you:
1) select the code to enclose
2) click the # button in the menu mentioned above
(You'll see an example of how this looks a bit down in this post)

About running Compendium:
The start script assumes you are launching it from the same directory as it's in, so you'll have to edit the script to change to that dir before launch.
1) open compendium.sh in a text editor
2) replace original contents with this (I added three lines before the java command):
```
#!/usr/bin/env bash
DIRECTORY=$(cd `dirname $0` && pwd)
cd $DIRECTORY
java -Xmx256m -cp .:System/lib/compendium.jar:System/lib/compendiumcore.jar:System/lib/AppleJavaExtensions.jar:System/lib/compendiumrecordcontrol.jar:System/lib/triplestore.jar:System/lib/xml.jar:System/lib/kunstoff.jar:System/lib/jabberbeans.jar:System/lib/jhall.jar:System/lib/mysql-connector-java-3.0.11-stable-bin.jar:System/lib/derby.jar com.compendium.ProjectCompendium %1 %2 %3 %4 %5 %6 %7 %8 %9
```
3) save the file
Voila now you can launch the program by just double-clicking compendium.sh

---

### Post by paparon on 2011-03-20
Thanks lykeion,

I pasted the first three lines in above the java command but still get the same results: ```
Exception in thread "main" java.lang.NoClassDefFoundError: com/compendium/ProjectCompendium
Caused by: java.lang.ClassNotFoundException: com.compendium.ProjectCompendium
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: com.compendium.ProjectCompendium. Program will exit.
```

Thanks for explaining the # button.

---

### Post by lykeion on 2011-03-21
That's strange because I actually tried it myself and it worked fine.

Try to change the java line in the script to the line from my post above, i.e. not just add the first three lines.

I can't remember if it was the 1.5.2 or the 2.0b1 version I tried. Have you tested with both?

---

### Post by paparon on 2011-03-21
Problem solved! 

1st I copied and pasted your whole code as you suggested and had the same problem. Then a light went on and I logged in as root and Compendium sort of ran. I had installed it as root because I wanted it in /usr/bin. I moved it and unpacked it with Nautilus. 

I deleted that installation, signed in as me, re-unpacked it using the command line, moved it to /usr/bin with "sudo mv" and now it works fine.

I guess I learn best by making mistakes. Thanks for your help, lykeion. It was your telling me that you tried it yourself and it worked fine that made me think that how I unpacked it might be the problem.

Oh, and yes, it needed those three lines of code to run from the launcher I created.

Thanks again.

---

