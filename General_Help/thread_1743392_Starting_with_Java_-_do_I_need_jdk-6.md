---
title: "Starting with Java - do I need jdk-6?"
date: 2011-04-29
forum: General Help
---

### Post by Wealdey on 2011-04-29
Hi,

I've been running Ubuntu (10.10 - 32 bit) for about 3 months. Being curious about the very basics of Java programming I've just installed Netbeans 6.9 through the Ubuntu software centre and done the "Hello World" exercise within Netbeans. The file is in my Home folder but I'm not clear how now to try and run it. 

Some Googling has raised some contradictory recommendations about adding the Sun/Oracle repository and the installing JDK6 as well. I'm now getting out of my depth so if someone can share knowledge on where to go from here I would be grateful.

PS: Have just registered so I hope this post is expressed correctly.

---

### Post by GregBrannon on 2011-04-29
It's expressed fine.

You should check out the Programming Talk sub-forum: [http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39").  The forum has many threads from those asking about the early stages of getting started programming to more advanced help, and there are stickies at the head of the forum, kind of an FAQ collection, that answer many of the beginner's questions.

As for which version of Java to use, I assume you're asking if the Open Java is okay or if you should use the Sun/Oracle version.  For learning, especially in the very early stages, it doesn't matter.  Later, when you're distributing your programs and want to be sure you have maximum compatibility with all platforms and OSs, you'd want to use the latest Java version from the source most widely used.  There are further complications if developing for Apple, but you won't have to worry about those considerations for a while.

Happy coding!

---

### Post by EarlsFurniture on 2011-04-29
I remember when I took my Java class that we had to make sure we  downloaded the all-inclusive Netbeans version.  (it is possible I think  to download it without the JRE or the JDK, I don't remember which, I  haven't touched it since.)  So if you got the truncated version, yes you will have to download whatever is missing for full functionality.

As for running your app, you should be able to do so from within Netbeans with no problem.  There should be an icon on the toolbar for it.  I think there is a "build" and a "build & run" option.

If you want to run it from the CLI, use:

```
java -jar /path/to/helloworld.jar
```

If the JRE is installed, it should also run by double clicking the file in Nautilus, as long as you have set execution permissions on it.

You can also create a shortcut with the above java command if you like as the target.

---

