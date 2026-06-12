---
title: "Not Able to Run Java Program From Eclipse"
date: 2010-01-26
forum: General Help
---

### Post by parmendratyagi on 2010-01-26
Hi All,
I am new to Ubuntu 9.10(even new to linux). I was previously using Windows OS. i am currently facing problem to run program using eclipse. In Eclipse, you can open a Java Class which contains main method, right click and chose to "Run as --> Java Application". 

On Windows , it works fine. But when i am doing same in Ubuntu, Eclipse throws ClassNotFound Exception...

Here is Trace
---

Exception in thread "main" java.lang.NoClassDefFoundError: com/Main
Caused by: java.lang.ClassNotFoundException: com.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.Main.  Program will exit.



com.Main class contains main method..
About Eclipse i am using ---
Version: 3.5.1
Build id: M20090917-0800


Please help:(

---

### Post by t4thfavor on 2010-01-26
Java, Being not quite exactly cross platform from day one!

It appears the the JVM for windows has one more bugfix than the one for Linux. That or you accidentally messed it up.

I would bet more on the fact that closed source things for Linux (flash, java, nvidia) tend to be last on the dev lists for fixes.

EDIT:
I just thought of something else.

Try adding a definition for main at the top of the file. possibly it is not optional under Linux.

Or

[http://www.jguru.com/faq/view.jsp?EID=455768](http://www.jguru.com/faq/view.jsp?EID=455768)

---

### Post by parmendratyagi on 2010-01-26
> **t4thfavor said:**
> Java, Being not quite exactly cross platform from day one!

It appears the the JVM for windows has one more bugfix than the one for Linux. That or you accidentally messed it up.

I would bet more on the fact that closed source things for Linux (flash, java, nvidia) tend to be last on the dev lists for fixes.

EDIT:
I just thought of something else.

Try adding a definition for main at the top of the file. possibly it is not optional under Linux.

Or

[http://www.jguru.com/faq/view.jsp?EID=455768](http://www.jguru.com/faq/view.jsp?EID=455768)
I didn't get you here.... Could you pls explain

---

### Post by chessnerd on 2010-01-26
First, make sure you have both the JRE and JDK installed:
```
apt-get install sun-java6-jdk sun-java6-jre
```

Or, if you'd prefer OpenJDK:
```
sudo apt-get install openjdk-6-jdk openjdk-6-jre
```

(Not 100% sure about those install commands, so you could just grab those from the Software Center if the commands don't work.)

Also, I had some issues when using the Eclipse from the Software Center. If you got Eclipse from the Ubuntu Software Center or Add/Remove... you could try removing it and installing Eclipse from the terminal with:

```
sudo apt-get install eclipse
```

Hope this helps.

---

### Post by parmendratyagi on 2010-01-26
> **chessnerd said:**
> First, make sure you have both the JRE and JDK installed:
```
apt-get install sun-java6-jdk sun-java6-jre
```

Or, if you'd prefer OpenJDK:
```
sudo apt-get install openjdk-6-jdk openjdk-6-jre
```

(Not 100% sure about those install commands, so you could just grab those from the Software Center if the commands don't work.)

Also, I had some issues when using the Eclipse from the Software Center. If you got Eclipse from the Ubuntu Software Center or Add/Remove... you could try removing it and installing Eclipse from the terminal with:

```
sudo apt-get install eclipse
```

Hope this helps.
I hava sun-java6-jdk install. It is working fine.

I install Eclipse using "Synaptic Package Manger". 
did your mean, this could have problem itself ?

---

### Post by t4thfavor on 2010-01-26
Just throwing out possible answers for you as you had it working under Windows, and with Java being a C syntax language, I thought that maybe you had to add a definition to the top of the source file.

like 

function main(int, int);

Im not sure of the java syntax exactly, but the other post seems more likely the cause. Also check out that link as they say you need to setup the class path correctly.

At least it's a start in the correct direction.

---

### Post by parmendratyagi on 2010-01-26
> **t4thfavor said:**
> Just throwing out possible answers for you as you had it working under Windows, and with Java being a C syntax language, I thought that maybe you had to add a definition to the top of the source file.

like 

function main(int, int);

Im not sure of the java syntax exactly, but the other post seems more likely the cause. Also check out that link as they say you need to setup the class path correctly.

At least it's a start in the correct direction.
Thanks for your help & time..
I am sure about the syntax is correct...

---

### Post by t4thfavor on 2010-01-26
> **parmendratyagi said:**
> Thanks for your help & time..
I am sure about the syntax is correct...

I meant my function definition syntax, I don't do java.

---

### Post by jtuchscherer on 2010-01-26
it would be easier to help you if you could send a screenshot of your eclipse workspace with your class that you want to run open.
From looking at the error message I would assume you messed something up with the package name. Is your class in the right folder?

---

### Post by teward on 2010-01-26
I had issues with Eclipse and Java previously.  Here's what I did to fix it:  I didn't install Eclipse from the repos.  I just downloaded the .tar.gz file from the Eclipse website, extracted to a folder in my /home folder, and it works like a charm.

If you've got issues when using Eclipse and Java, its quite possible that the issue is in the version of Eclipse (hence why I downloaded the files and untar'd them)

[http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by parmendratyagi on 2010-01-26
Here you go... & Thanks for your time...

---

### Post by parmendratyagi on 2010-01-26
> **TrekCaptainUSA said:**
> I had issues with Eclipse and Java previously.  Here's what I did to fix it:  I didn't install Eclipse from the repos.  I just downloaded the .tar.gz file from the Eclipse website, extracted to a folder in my /home folder, and it works like a charm.

If you've got issues when using Eclipse and Java, its quite possible that the issue is in the version of Eclipse (hence why I downloaded the files and untar'd them)

[http://www.eclipse.org/](http://www.eclipse.org/)
I am going to try that also..

---

### Post by parmendratyagi on 2010-01-26
> **parmendratyagi said:**
> I am going to try that also..
This is also not working...Now i am getting below exception....:(

Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/equinox/launcher/Main
Caused by: java.lang.ClassNotFoundException: org.eclipse.equinox.launcher.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: org.eclipse.equinox.launcher.Main. Program will exit.

---

### Post by jtuchscherer on 2010-01-26
> **parmendratyagi said:**
> Here you go... & Thanks for your time...

Did you try to compile the class first?

---

### Post by parmendratyagi on 2010-01-26
> **jtuchscherer said:**
> Did you try to compile the class first?
Eclipse is the auto compilation and i also cross checked the bin directory.
.class are present there.

---

### Post by parmendratyagi on 2010-01-27
Hi All,
I have the solution of this problem. Actually i have while install linux i made 3 partition. I install linux on one partition and using another partition to store data. 
I have create the workspace on the one of them partition (partition on which linux is not install).. 

I move the workspace under /home/user_name/ and it start working.

Thank you all for your time.

---

