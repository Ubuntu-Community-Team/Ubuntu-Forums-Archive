---
title: "Having trouble installing MySQL Connector J"
date: 2010-06-27
forum: General Help
---

### Post by Initsil on 2010-06-27
Hey everyone. 

I followed this tutorial([https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)) to install mysql-connector-java. Although, I can't get it to work. It keeps saying that I need to install it. 

Here's my CLASSPATH output:

```
root@hostname:~# echo $CLASSPATH
.:/usr/share/java/mysql.jar
```

Any help is appreciated.

---

### Post by thebigob on 2010-06-27
Though you have the file in the classpath is it actually there?

```

ls /usr/share/java | grep mysql.jar

```

if you get no output you need to download the jar

---

### Post by forestG on 2010-06-27
> **Initsil said:**
> Hey everyone. 

I followed this tutorial([https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)) to install mysql-connector-java. Although, I can't get it to work. It keeps saying that I need to install it. 

Here's my CLASSPATH output:

```
root@hostname:~# echo $CLASSPATH
.:/usr/share/java/mysql.jar
```

Any help is appreciated.

Create a worskpace folder where you have inside all your code (*.java) files and class files. inside that folder you should also create a lib folder where you store all you lib files.Put all you lib files in that folder. Since you use mysql you should have inside that folder the file mysql-connector-java-5.1.12-bin.jar or something like that. 
If you compile and run your code through shell using the javac/java commands define your classpath explicitly using -cp flag.  That is java(c) -cp /path/to/your/lib/files etc..
However I suggest that you create your code through an IDE such as Eclipse or NetBeans. Using those IDE's makes including lib files very easy. 
And if you want to run them outside Eclipse/NetBeans just create a jar file and you are set. Creating runnable jar files is a piece of cake when you use either Eclipse or NetBeans.  

Important note: I suggest that you don't install Eclipse through the Ubuntu Software Center or Synaptic. It would be better if you just download it, uncompress it in a folder and run it. When I installed it through Ubuntu software center it did not work very well. It is much better if you have all your IDE's files in a folder because the configuration is so much easier.

---

### Post by Initsil on 2010-06-27
I just ran this command and I think I got the correct output

```
root@hostname:~# ls /usr/share/java | grep mysql.jar
mysql.jar

```

Also, this isn't a project that I'm building. It's a java project that's already been compiled and I'm downloading it off the web.

---

### Post by forestG on 2010-06-29
> **Initsil said:**
> I just ran this command and I think I got the correct output

```
root@hostname:~# ls /usr/share/java | grep mysql.jar
mysql.jar

```

Also, this isn't a project that I'm building. It's a java project that's already been compiled and I'm downloading it off the web.

download the jdbc driver from the mysql site [http://www.mysql.com/downloads/connector/j/](http://www.mysql.com/downloads/connector/j/)
and call the java command with -cp /absolut/path/to/jdbc/driver.

---

