---
title: "something goes wrong when I try to run java .class files"
date: 2009-10-05
forum: General Help
---

### Post by Oblivion4 on 2009-10-05
Why hello there!
I seem to be having some trouble running .class files from bash. At first I thought I was just a complete retard and forgot to how to but it seems that the problem is a bit more complicated. However I am able to compile java programs. 

For example. Lets save I have a program like this

```
public class yourmom
{


     public static void main(String[] args)
     {
             while(true)
             {
                     System.out.println("your mom loves my phallus");
             }
     }

}

```I am able to compile the .class file but not run it. I know the problem is probably an environment variable or a program thats not installed. I am fairly sure that I have the runtime installed because I can run programs like openoffice. Any help would be appreciated.

I should also mention the error I receive when i try to run the program. I get the generic class cannot be found error shown here.

Exception in thread "main" java.lang.NoClassDefFoundError: yourmom
Caused by: java.lang.ClassNotFoundException: yourmom
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: yourmom. Program will exit.

---

### Post by dearingj on 2009-10-05
What is the exact command line you use to run the program? It sounds to me like it's not looking in the right directory.

---

### Post by Oblivion4 on 2009-10-05
java nameofprogram. I also tried java ./nameofprogram which did not work

---

### Post by The Cog on 2009-10-05
And how did you compile it? Please can you post the commands you used both to compile it and to run it. Don't try to filter the output - include the commands and all their output and the prompts. Your hiding information from us only hinders finding the problem.

---

