---
title: "compiling .java file to native executable"
date: 2012-06-21
forum: General Help
---

### Post by Und3rH3ll on 2012-06-21
Hi everyone.I am new to ubuntu.Is there any method to compile the java file into native executable form,so that  it can be run on other machine without installing jdk?
Thanks in advance.

---

### Post by hunter.allen on 2012-06-21
Java works out of a virtual machine, so I don't see a way of creating an executable without (at minimum) the JRE package installed. When using a java file, it creates a compiled ".class" file. This is what JRE runs. On windows, you run a .jar file. 

Here is an excellent link for your [question]("http://www.linuxjournal.com/article/4860?page=0,0").

---

### Post by Gyokuro on 2012-06-21
Hi

With Excelsior's JET you should achieve your goal: [http://www.excelsior-usa.com/jet.html](http://www.excelsior-usa.com/jet.html)

but it is better you bundle your java app with a JRE and transfer it as a complete package.

---

