---
title: "J2EE Question"
date: 2009-08-04
forum: General Help
---

### Post by mthalis on 2009-08-04
In order to run j2ee application in Ubuntu, I install java using 
```
sudo apt-get install <java6>
```

But I couldn't find j2ee.jar in my machine. Please explain how can I fix this problem.

---

### Post by prshah on 2009-08-04
> **mthalis said:**
> In order to run j2ee application in Ubuntu, I install java using 
```
sudo apt-get install <java6>
```

But I couldn't find j2ee.jar in my machine. 

j2ee cannot be installed from the repositories; try netbeans instead; or you can get the j2ee binary (.bin) from the sun website and install it.

---

### Post by kpkeerthi on 2009-08-04
[http://www.netbeans.org/downloads/index.html]("http://www.netbeans.org/downloads/index.html")

[http://www.eclipse.org/home/categories/index.php?category=enterprise]("http://www.eclipse.org/home/categories/index.php?category=enterprise")

[http://www.jboss.org/projects/matrix]("http://www.jboss.org/projects/matrix")

---

### Post by mthalis on 2009-08-04
I installed j2ee using below link
> [http://java.sun.com/javaee/downloads/index.jsp?userOsIndex=1&userOsId=linux&userOsName=Linux](http://java.sun.com/javaee/downloads/index.jsp?userOsIndex=1&userOsId=linux&userOsName=Linux)

It installed /home/ites/SDK folder

What is next step should I do? Should I set CLASSPATH and JAVA_HOME ?

Note - I already installed Java 6 using **apt-get install**

---

### Post by arch0njw on 2009-08-04
> **mthalis said:**
> I installed j2ee using below link


It installed /home/ites/SDK folder

What is next step should I do? Should I set CLASSPATH and JAVA_HOME ?

Note - I already installed Java 6 using **apt-get install**

There are a couple of ways.  I usually create a small script to run whatever it is that needs specific JAR files.  You can also edit either your .profile or .bashrc to update these environment variables.

I'm not quite clear on what you are trying to do, so I'll talk about .profile and .bashrc.  In either file you can modify your classpath and set java_home.  Edit either one of those files and add the following line:
```
CLASSPATH=$CLASSPATH;/path/to/j2ee.jar; export CLASSPATH
```You shouldn't need to set JAVA_HOME since you installed the Java 6 package.  If you need to, you need to find the actual java install directory and set JAVA_HOME to the actual install root of java.  I found this on my system by doing the following:
1. which java
2. returned "/usr/bin/java"
3. ls -lF /usr/bin/java
4. which showed me it was a link to somewhere else
5. ls -lF /etc/alternatives/java
6. which showed me THAT was a link to somewhere else, but it was where I wanted:  **/usr/lib/jvm/java-6-openjdk**/jre/bin/java.  The part I made bold is the "JAVA_HOME" you would set (JAVA_HOME=/usr/lib/jvm/java-6-openjdk; export JAVA_HOME)

You then might want to update your PATH to include $JAVA_HOME/bin.
PATH=$PATH;$JAVA_HOME/bin; export PATH

You can then double-check all of this from the command line with "echo":
1. echo $CLASSPATH
2. echo $JAVA_HOME
3. echo $PATH

Hope that helps.

---

### Post by mthalis on 2009-08-04
What I want is configure my environment to run j2ee application without using IDE(ejb application)

---

### Post by arch0njw on 2009-08-04
> **mthalis said:**
> What I want is configure my environment to run j2ee application without using IDE(ejb application)

Updating your .profile or .bashrc will do that for you.  You might need to restart Gnome (logout, login) to get the shell to pick up the variable change.

I did forget to mention that one way to test these changes is to open a new gnome-terminal.  That rereads these files and will show you if the changes are really in place.

---

### Post by mthalis on 2009-08-05
Thank you everyone,
Here how I did it.

First I downloaded and installed java6 using **apt-get install**
Next downloaded **j2ee** and installed

Next I set my path in **.bashrc** file

> 
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.14
export JAVA_HOME

PATH=$PATH:$JAVA_HOME/bin;

CLASSPATH=/usr/lib/jvm/java-6-sun-1.6.0.14/lib
CLASSPATH=$CLASSPATH:/home/ites/SDK/lib/j2ee.jar;
export CLASSPATH

 

Thank you.

---

