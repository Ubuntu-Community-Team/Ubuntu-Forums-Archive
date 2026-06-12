---
title: "Java error"
date: 2006-04-13
forum: General Help
---

### Post by the_tiger on 2006-04-13
I have been writing a simple program which involves string concatenation. The class is called ImprovedFibonacci. Compilation using javac is fine. When I simply type *java ImprovedFibonacci* I get the errors:

Exception in thread "main" java.lang.NoClassDefFoundError: while resolving class: ImprovedFibonacci
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: java.lang.StringBuilder not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   ...4 more

however if I use java from /usr/lib/j2sdk1.5-sun/bin/java it works fine.

Please help. Why is this version of java not working? How do I use the Sun version by default?

---

### Post by Ensnared on 2006-04-13
Can't tell you what's wrong with the other version, but I always use the Sun Java since that's always been the only thing that's worked for the few Java applications I use.

To make it the default, you do this:
```
sudo update-alternatives --config java
```
Select Sun's JRE by typing the appropriate number, and Bob's your uncle :)

---

