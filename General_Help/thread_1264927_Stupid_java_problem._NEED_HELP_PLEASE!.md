---
title: "Stupid java problem. NEED HELP PLEASE!"
date: 2009-09-12
forum: General Help
---

### Post by ocin24 on 2009-09-12
Hi there...

So i just installed Ubuntu last week and was interested in picking up Java again ( I began learning it a few years ago...)

So I installed the most recent version of JDK and Eclipse. I was having no problems compiling and running .class's i created with Eclipse as long as they were in the "default package" folder (main project folder). 

Eclipse suggested that it was not recommended to save files directly in the Project folder, that I should create a new package, and I thought that was a good idea since it would help organize my programs anyway.

It seemed to be working fine, I compiled and ran a few progs from the new subfolder (~/workspace/******* Around/Chapter1), no sweat. All of a sudden, the java *className* function stopped working! I can navigate to the main Project folder and run classes fine! I tried update-java-alternatives, but that was fine and didn't seem like the problem anyway...

Anyways, I'm sure I'm in the right dir and I'm pretty sure I'm typing the commands correctly. Am I doing something wrong? Can I not divide projects into these side-"Packages"?

Oh yea, here's what I'm getting from the terminal:
```
user@Computer:~/workspace/******* Around/Chapter1$ java Exercise1
Exception in thread "main" java.lang.NoClassDefFoundError: Exercise1 (wrong name: Chapter1/Exercise1)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: Exercise1.  Program will exit.
```

Any idea or solutions would be greatly appreciated. :)

EDIT:
I forgot to mention, I'm sure the .java compiled correctly. Or at least *ls* reveals Exercise1.java AND Exercise1.class...

---

### Post by falconindy on 2009-09-12
If you're importing classes that aren't part of the default classpath, you'll need to specify that in the execution. i.e.:
```
java -cp /path/to/other/classes Exercise1
```

---

### Post by ocin24 on 2009-09-12
> **falconindy said:**
> If you're importing classes that aren't part of the default classpath, you'll need to specify that in the execution. i.e.:
```
java -cp /path/to/other/classes Exercise1
```

To begin, thank you for helping. :D

Now, I tried your suggestion, I tried typing the relative and absolute paths from both the main project folder and the subfolder. Any way I type it, it gives me the Java help printout for using Java (not the man). 

I read through both this and the man and I can't figure out for the life of me what's wrong. 

location of .class: /home/user/workspace/******* Around/Chapter1
I tried:
```
java -cp /home/user/workspace/******* Around/Chapter1 Exercise1
java -cp /home/user/workspace/******* Around/Chapter1/Exercise1
java -cp /home/user/workspace/******* Around/Chapter1/Exercise1.class
java -cp /Chapter1 Exercise1
java -cp /Chapter1/Exercise1
java -cp /Chapter1/Exercise1.class
```
I tried all of these from both the main project dir (******* Around) and the subfolder (changing the relative paths accordingly) and NOTHING! I get the help dialog when I use the "/" before the class name and when I don't, the same error as before!

Any other ideas?

EDIT: 
And before anyone asks, I DID escape the space when i put that in the terminal. :P

---

### Post by falconindy on 2009-09-12
Maybe I'm misunderstanding what's going on here. I'm definitely not going to rule that out. Is your source code referencing another library that you wrote? Are you trying to execute the class with main() from outside the directory where it resides?

In essence, when you execute `java`, the classpath needs to encompass everything that your bytecode references. Now, that may comprise a mix of user defined and built-in libraries, but **every** directory needs to be involved in that classpath.

Here's an example. I've got a class called HelloWorld in ~/dev/java. From my home root, I can do this:
```
java -cp dev/java/ HelloWorld
```And it'll run happily. Let's say HelloWorld runs in some homegrown dialog box I've created in a subdirectory of ~/dev/java. Again, I can run it from ~/ as follows:
```
java -cp dev/java/:dev/java/dialog/ HelloWorld
```And now my classpath covers the base class file with main(), and it also references the extra dialog class that I've written and that resides at the relative path 'dev/java/dialog/'. If i was already in ~/dev/java/ when I wanted to run HelloWorld, it would be simpler:
```
java -cp dialog/ HelloWorld
```I only need to reference the subdirectory dialog/ because  the present working directory is included by default.

Hope this helps (and makes sense)!

---

### Post by ocin24 on 2009-09-12
Ugh... This is annoying me and I know it's going to end up being some stupid thing I'm doing wrong...

So I'm not loading any libraries at all, let alone any user-defined ones. I'm going over the most basic little programs in the world (on par with HelloWorld...) 

I tried your last example before and now again (with some minor syntax tweaks yours had that were different from mine) e.g. ```
java -cp Chapter1/ Exercise1
``` instead of ```
java -cp /Chapter1 Exercise1
``` with the same result.

The PWD is in the dir directly above Chapter1, where the class is stored. For some reason, the java will run classes in the upper dir no problem but then won't touch the classes in the subfolder! No matter where I move the PWD to access them! I feel like I've attacked this from every angle! :(

---

### Post by falconindy on 2009-09-12
Post your source code.

---

### Post by ocin24 on 2009-09-12
Okay, I hadn't noticed this before, but when I moved the prog into the new subdirectory with eclipse, it adds the package line before the class:

```
package Chapter1;


public class Exercise1 {
	public static void main(String args[]) {
		int num = 1000;
		System.out.println(num + " is the value of num");
	}

}

```

Does this change something? When I try to remove this line, Eclipse throws me an error:

> 
The declared package "" does not match the expected package "Chapter1"	******* Around/Chapter1	Exercise1.java	line 1	

So I can't change that...
:(

---

### Post by falconindy on 2009-09-12
Aha! I saw that error and it got me thinking... glad I asked for source.

No problem. You can leave in the package declaration. What java wants is the fully qualified name of the class. In this case, It's Chapter1.Exercise1. However, there's a catch. Your directory structure needs to match this hierarchy. So, Exercise1.class needs to reside in the directory Chapter1. You'll then be able to execute the damn thing one level up from the Chapter1 directory with just:
```
java Chapter1.Exercise1
```Packages are a real pain in the butt for small bits of code, but getting used to using them is amazingly convenient if and when your program ends up as a lot of files.

Also, this is why I don't use Eclipse ;P

---

### Post by ocin24 on 2009-09-12
OMG!

I knew it was something relatively trivial... Thank you SO MUCH for sticking with me through this, I'm still getting used to a UNIX based OS and trying to get everything functioning, although I guess this was a problem with Eclipse...

Anyways, everything is working splendidly now. :D

Thanks again!

---

