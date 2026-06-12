---
title: "Need help with a java program"
date: 2009-07-13
forum: General Help
---

### Post by Cotopaxi on 2009-07-13
Hi!

I have a Java program called "Zettelkasten". Within the directory of the program, I opened a terminal and typed: "java -jar ./Zettelkasten.jar. It has worked fine for two weeks but, after one System update, I am getting the following output:

> no@no-laptop:~/AB Software/Zettelkasten/Zettelkasten3$ java -jar ./Zettelkasten.jar
Exception during event dispatch:
java.lang.NoClassDefFoundError: zettelkasten.ZettelkastenView
   at java.lang.Class.initializeClass(libgcj.so.90)
   at zettelkasten.ZettelkastenApp.startup(ZettelkastenApp.java:76)
   at org.jdesktop.application.Application$1.run(Application.java:171)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.90)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.90)
   at java.awt.EventDispatchThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: javax.swing.RowSorter not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./Zettelkasten.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...5 more
no@no-laptop:~/AB Software/Zettelkasten/Zettelkasten3$


Can anyone give me a helping hand please?

Thanks! :p

---

### Post by Cotopaxi on 2009-07-13
Does anyone know a forum with "java propellerheads"? :)

---

### Post by ddrichardson on 2009-07-13
Have you tried this with Sun Java?

[http://is.gd/1xz72](http://is.gd/1xz72)

---

### Post by Cotopaxi on 2009-07-14
ddridchardson,

your link solved it! Thanks very much indeed!!!:popcorn:

Just to resume, what was the trick: you select sun-java to be run by default. To achieve this, one only has to type in terminal:

[HTML]sudo update-java-alternatives -s java-6-sun[/HTML]

Thanks again!

---

