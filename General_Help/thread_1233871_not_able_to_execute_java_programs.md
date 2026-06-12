---
title: "not able to execute java programs"
date: 2009-08-07
forum: General Help
---

### Post by shashi859 on 2009-08-07
i hav installed java-6-openjdk. i m not able to execute the program, i hav followed the steps as specified but they are not working. when i tryed to execute the file sqrrt using the following command it shows like this,

shiva@shiva-desktop:~$ javac sqrrt.java
File sqrrt.java is missing

plz help me how to get corrected.

---

### Post by snek on 2009-08-07
Try:

javac ./sqrrt.java

Somehow Linux is picky with adding ./ if you are trying to use a file in the directory you are currently in.

---

### Post by fennec_fox on 2009-08-07
This may not be helpful but, make sure you are in the right directory and are spelling it exact. Make sure the capital letters are right. It seems to be able to find javac so java is installed right. It just can't find the file so it's looking in the wrong directory, the file name is spelled wrong or you'll need to try what snek said. 

Next time you try it make sure you are in the right folder and type 
javac sq  

then hit tab a couple times to see the names of files in that folder starting with sq. This should make sure it's spelled right. If it doesn't find anything it's a folder or capital letter issue. sqrrt might start with a capital S so it doesn't find it.

---

### Post by shashi859 on 2009-08-07
thanks Sneak. but, after trying ur suggestion i got this problem.


shiva@shiva-desktop:~/java$ javac ./sqrrt.java
shiva@shiva-desktop:~/java$ java sqrrt
Exception in thread "main" java.lang.NoClassDefFoundError: sqrrt
Caused by: java.lang.ClassNotFoundException: sqrrt
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: sqrrt.  Program will exit.
how to come out of this?

---

### Post by fennec_fox on 2009-08-07
Try
**java -classpath ****sqrrt**

It appears it can't find the class path.

---

### Post by khelben1979 on 2009-08-07
Have you installed java [from java.com]("http://www.java.com/en/download/index.jsp")?

---

### Post by shashi859 on 2009-08-08
:D [SIZE=2][FONT=Century Gothic]Thanks to everyone for suggestions. My java software installation was correct and everything else was also correct. The problem appeared because i made mistake by typing,
[/FONT]
 shiva@shiva-desktop:~$ java sqrrt

[FONT=Comic Sans MS]instead of typing correctly as [/FONT]

shiva@shiva-desktop:~$ java squareroot

[FONT=Comic Sans MS]That is instead of typing the class name "square root" which compiler  used to create .class file, i always kept trying with the file name i have created.  Now i m able to run programs. Once again thanks to everyone for suggestion.[/FONT][/SIZE]

---

