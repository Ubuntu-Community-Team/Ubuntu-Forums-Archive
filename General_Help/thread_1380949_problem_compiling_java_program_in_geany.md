---
title: "problem compiling java program in geany"
date: 2010-01-14
forum: General Help
---

### Post by sridarshan on 2010-01-14
i installed javac in my ubuntu,i use geany to write java programs,when i wrote a test program in geany,it compiled properly,but when i ran the program it gave a following error
```
exception in thread main java.lang.noclassdeffounderror
```
how do i get rid of this?

---

### Post by john newbuntu on 2010-01-14
You need to define the classpath either via an environment variable or an argument to your program in order for java runtime to see the bytecode.  Please read up on Classpath.

---

### Post by sridarshan on 2010-01-14
and how do i do that?

---

### Post by john newbuntu on 2010-01-14
Your answer lies towards the last part of this document:
[http://java.sun.com/docs/books/tutorial/getStarted/problems/index.html](http://java.sun.com/docs/books/tutorial/getStarted/problems/index.html)

---

### Post by sridarshan on 2010-01-15
they said 
```
A common mistake made by beginner programmers is to try and run the java launcher on the .class file that was created by the compiler. For example, you'll get this error if you try to run your program with java HelloWorldApp.class  instead of java HelloWorldApp.
```
actually thats the way i tried to execute the program

---

