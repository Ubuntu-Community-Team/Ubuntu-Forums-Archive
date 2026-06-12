---
title: "Java"
date: 2009-11-25
forum: General Help
---

### Post by accooper on 2009-11-25
I have some Java programs that I would like to run in Ubuntu, but I just can't get them to run.  Any help here?

TIA
Andrew From Texas

---

### Post by Mr. Devil on 2009-11-25
Applications / Accessories / Terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

Then just double-click on the JAR file ( your application ) and it should work just fine.

---

### Post by t0p on 2009-11-25
First of all you need to install the Java Runtime Environment.  Open a terminal and type in the command:

```
sudo apt-get install sun-java6-jre
```

Now, to run a Java program:

In a folder called freedom, I have a Java app called freedom.jar.  To run it, I type into a terminal:

```
java -jar freedom/freedom.jar
```

You should be able to modify that to suit your situation.

---

### Post by accooper on 2009-11-25
Nope, neither idea worked.

I did get the plugin suggested to install, but when I double clicked, all it did was unpack the .jar file, and I also tried the second suggestion but it said no such file.  How do I get to the folder my jar files are in?

They are in:

/media/DATA 2/Open Rocket

Andrew

---

### Post by abhishek.malhotra35 on 2009-11-25
Try installing jdk instead of jre. Also you have to set path for java. If you are installing using apt-get then run below command:
sudo update-alternatives --config java.

If you are installing binary then you need to set path manually.

---

### Post by Mr. Devil on 2009-11-25
```
cd "/media/DATA 2/Open Rocket"
ls
[COLOR=Gray]-- here you see the list of files in /media/DATA 2/Open Rocket --
-- take one of the filenames and proceed with the next command ( replace filename.jar ) --[/COLOR]
java -jar filename.jar
```

If the below route doesn't work, try without the -jar parameter ( for .class files ).

> **abhishek.malhotra35 said:**
> Try installing jdk instead of jre. Also you have to set path for java. If you are installing using apt-get then run below command:
sudo update-alternatives --config java.

If you are installing binary then you need to set path manually.

JDK isn't necessary for running Java applications.

---

### Post by abhishek.malhotra35 on 2009-11-25
> **Mr. Devil said:**
> ```
cd "/media/DATA 2/Open Rocket"
ls
[COLOR=Gray]-- here you see the list of files in /media/DATA 2/Open Rocket --
-- take one of the filenames and proceed with the next command ( replace filename.jar ) --[/COLOR]
java -jar filename.jar
```

If the below route doesn't work, try without the -jar parameter ( for .class files ).



JDK isn't necessary for running Java applications.
First of all, for running jar file, -jar option has to be used. Clearly if the person is not able to run jar using this command, then either paths are not set or you might have to install jdk. I understand jdk is not required to run java applications. The issue can be with PATH and CLASSPATH.

---

### Post by abhishek.malhotra35 on 2009-11-25
BTW, what are you getting when you are executing below line?

java -jar freedom.jar

---

### Post by Mr. Devil on 2009-11-25
> **abhishek.malhotra35 said:**
> First of all, for running jar file, -jar option has to be used. Clearly if the person is not able to run jar using this command, then either paths are not set or you might have to install jdk. I understand jdk is not required to run java applications. The issue can be with PATH and CLASSPATH.

The problem here is that we don't know wether he have a JAR or CLASS file. If it doesn't work with -jar, another guess would go for a plain class file which should be launched without the -jar paremeter.

> **abhishek.malhotra35 said:**
> BTW, what are you getting when you are executing below line?

java -jar freedom.jar

You are now referring to someone elses example and I doubt the OP have this file/application.

---

### Post by abhishek.malhotra35 on 2009-11-25
> **Mr. Devil said:**
> 
You are now referring to someone elses example and I doubt the OP have this file/application.

Yes I am referring to another person example as he only suggested to run that code. So I assume he knows that it is a jar file(as the user haven't mentioned whether he hads a jar file or class file).

> **Mr. Devil said:**
> 
The problem here is that we don't know wether he have a JAR or CLASS file. If it doesn't work with -jar, another guess would go for a plain class file which should be launched without the -jar paremeter.
I agree with you..

---

