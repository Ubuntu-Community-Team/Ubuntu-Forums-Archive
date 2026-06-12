---
title: "Problem Running .class Files With Oracle Java 1.7.0_05"
date: 2012-07-15
forum: General Help
---

### Post by zaza224 on 2012-07-15
I am a new Java programmer running Oracle JDE 1.7.0_05 and Oracle JDK 1.7.0_05. I wrote a simple program : 
public class MyFirstApp {

    public static void main (String[] args) {
          System.out.println("I rule,");
          System.out.println("The world!");
        }



}

I ran it through the compiler using the "javac" command and it ran through with no problems. However, when I try to run the resulting .class file using the "java" command, I get the following message: "Error: Could not find or load main class MyFirstApp".  Why is this happening?

---

### Post by violinuxer on 2012-07-15
What were the commands you ran? This could be cause by quite a few different issues.

Before continuing, post the output of these commands to show which java versions are installed / running:

```
"update-java-alternatives -l"

and

"java --version"
```Some things to check:

Make sure the jdk is installed properly. Given that ubuntu ships with java jre 1.6, it may be trying to run the class using JRE 6. Try looking at the manpages for update-java-alternatives to switch between 1.6 and 1.7

Make sure you are running the class file from the same directory.

Good luck!

violinuxer

---

### Post by BinaryLinux on 2012-07-15
When I first started java programming, I had the same problem. Instead of running 
```
java MyFirstApp**.class**
```
try it without the .class:
```
java MyFirstApp
```

Obviously, you should exclude <>, and use the name of your Java Project.

---

### Post by zaza224 on 2012-07-15
Thank you, but I figured out that before I could run the program, I had to direct the terminal to my program by typing: 

cd ~/Java

I'm very glad that it works now! :D Thank you for your time.

---

