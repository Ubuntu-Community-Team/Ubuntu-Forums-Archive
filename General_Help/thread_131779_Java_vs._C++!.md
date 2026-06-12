---
title: "Java vs. C++!"
date: 2006-02-17
forum: General Help
---

### Post by Leiki on 2006-02-17
I'm thinking of moving to Java, rather than C++. People told me most everybody chooses it over C++ and it's more flexible and...other things. What is your input on this? And if I do decide to make the switch, how could I write Java programs on Ubuntu?

---

### Post by boobytrapped on 2006-02-17
[QUOTE=Leiki]I'm thinking of moving to Java, rather than C++. People told me most everybody chooses it over C++ and it's more flexible and...other things. What is your input on this? And if I do decide to make the switch, how could I write Java programs on Ubuntu?[/QUOTE]

"Almost everybody chooses it" is definitely a generalization.  Both C++ and Java are great languages, and they have their own applications.  It basically depends on what kind of programs you are going to be writing.  

If you are just starting off with programming, its better to stick to Java.  Java manages the ugly low level details (such as memory management, pointers) for you.  On the other hand C++ puts you very close to the hardware.  C++ is definitely more "flexible", but that can be bad thing too (ie. its *very* easy to make mistakes -- with great power comes great responsibility.)

C++ is almost always going to be faster than Java.  Although the advances in [JIT]("http://en.wikipedia.org/wiki/JIT") technologies make Java pretty fast too.

For more details head over to wikipedia and learn a bit more both Java and C++.

---

### Post by mauriciorossi on 2006-02-17
[QUOTE=Leiki]I'm thinking of moving to Java, rather than C++. People told me most everybody chooses it over C++ and it's more flexible and...other things. What is your input on this? And if I do decide to make the switch, how could I write Java programs on Ubuntu?[/QUOTE]
nope stick with C++, java is still slower and will always be slower than C++
imo java can be easier for novices and C++ can be harder but, i started C++ when i was 12 so it cant be that hard :p 

Java is more portable, but C++ is stronger at most otherwise :-D

oh yea, i forgot to say, i signed up just to post this haha

---

### Post by slux on 2006-02-17
You could go either way, really depends on what kind of programs you're most interested in coding. Games would make you go towards C++ while java can even be easily used for web apps. Java's major disadvantage for now is that there is no complete free implementation (gcj is getting better and better though) and it does seem to me that java still is noticeably slow with complex apps.

---

### Post by davebradford on 2006-02-17
your not doing yourself any favors by using java if you already know c++, c++ is generally more used in industry, although you can knock something up in java faster than you ever could in c++.

have a look at the bluej java complier and see what you think.

[http://www.bluej.org/]("http://www.bluej.org/")

---

### Post by mr_mop on 2006-02-17
I'm not sure thats quite right.  I mean it depends on what industry you're in.
I'm in industry and I've been using C for 10 years. :)

---

### Post by slux on 2006-02-17
Well, C is still the most used programming language in the world. It's just that if there's some sort of migration happening, it's probably most towards C++.

---

### Post by rkakkar on 2006-02-17
i think Java rocks!! i'm into desktop application development and have been working in the industry for 6 months now. because of the portability of Java, creating our application for multiple platforms is the beauty. Plus java doesn't require you to get into the nitty-gritty of pointers to get a task done. sure ppl might say that its a language for the novices, but i think they do so only because it gets the job done simpler than to do the same task in C++

---

### Post by biguns on 2006-02-17
In Windowsland the migration is toward C#...

---

### Post by twigboy on 2006-02-17
yea and if you learn c# you get a little mix of java and c++

---

### Post by biguns on 2006-02-17
[QUOTE=twigboy]yea and if you learn c# you get a little mix of java and c++[/QUOTE]

*exactly...*

and it's not so verbose...

---

### Post by SteveF on 2006-02-17
It all depends on your goals.  What is it you're tyring to do.  Are you learning so that you can get a job?  I've seen more entry level Java jobs than entry level C++ jobs.  Are you trying to write particular type of application?  Some apps lend themselves better to one over the other and also depends on your own expertise?  What is your background?  You will find Java easier to learn than C++ coming from almost any other language except C or possibly Pascal.

If you give a little more information, I can offer some advice.  The one piece of adivce I will offer now is to give advice with extreme suggestions (such as "x is the best don't bother with y" or "x is too slow or y is too difficult") a wide berth.  Either language can be used to code many types of applications (there are always exceptions).

Steve

---

### Post by queenorych on 2006-02-17
What is better, an apple, orange, grapes?  They are just different.

Java -- sun gives away netbeans (ide, that is editor, compiler, debugger all in a nice window), and compiler, with semi-open license.  Java deals with freeing up memory when you are done.  Java is very structured such as (far as I know) requires you to have a new file for each class.

C++ -- g++ is a open source compiler.  Very good.  You allocate and free your own memory.

The real question is what do you want to do?  Is cross platform what you want?  Do you want to track the low level memory yourself? 

Libraries are a big deal for me.  Java has a nice set of libraries that are at least an attempt to being consistant, and complete.  wxwidgets is a great c++ library.  It allows you to natively compile native applications for linux/windows/mac/os2 etc.  Qt does the same.  Gnome/GTK does the same for C.

Don't listen to the garbage about java being slow.  I've seen studies showing java could be faster.  Most comments claiming Java is slow derive from the time when java wasn't compiled, but run through an interpreter.  That, and much of the slower calls have been optimized.  Moreover, do you really care if you helloworld snow man takes .000001 more seconds to come up.

---

### Post by mauriciorossi on 2006-02-17
[QUOTE=queenorych]
Don't listen to the garbage about java being slow.  I've seen studies showing java could be faster.  Most comments claiming Java is slow derive from the time when java wasn't compiled, but run through an interpreter.  That, and much of the slower calls have been optimized.  Moreover, do you really care if you helloworld snow man takes .000001 more seconds to come up.[/QUOTE]
Even when compiled java can be slow, plus anyways, java is only any better than C++ when it has to  be interpreted, which makes it slow

by the way, im pretty sure theyd rather use C++ than java in big blue lol


also, as far as libraries are concerned, fltk is really easy, like REALLY easy :-P

---

### Post by Leiki on 2006-02-19
@davebradford...

Thanks for your help (as well as everyone elses)! I think I'm going to stick to Java. Nothing really to lose, since I barely know C++ in the first place. After installing the JAR file of BlueJ by using ```
java -jar bluej-212.jar
``` it says ```
Failed to load Main-Class manifest attribute from bluej-212.jar
```. How do I fix it?

---

### Post by speedsix on 2006-02-20
Stick with Java, it's a much more modern, object oriented language.

Plus if you know java you know C#, hell I reckon you could copy/paste java code and it would work in C# *cough* clone *cough* ;)

---

### Post by slux on 2006-02-20
[QUOTE=biguns]In Windowsland the migration is toward C#...[/QUOTE]

In Microsoft's dreams maybe. If you're holding your breath for the programmers to mass-migrate to C# anytime soon, don't keep holding for too long because it's not going to happen anytime soon.

First of all it's much easier to get from C to C++ as C++ carries are the legacy payload of C and even that has taken ages while it's has been going on for a while already. Second, interpreted languages may eventually become the most used type but we're far, far away from that still.

You know, Java used to be the next big thing everyone was supposed to be learning but I'd say the hype has somewhat toned down and while it still has it's place no-one suggests that everyone would be using Java in a few years. It'll probably be the same with C#.

---

### Post by Lord Illidan on 2006-02-20
[quote=slux]In Microsoft's dreams maybe. If you're holding your breath for the programmers to mass-migrate to C# anytime soon, don't keep holding for too long because it's not going to happen anytime soon.

First of all it's much easier to get from C to C++ as C++ carries are the legacy payload of C and even that has taken ages while it's has been going on for a while already. Second, interpreted languages may eventually become the most used type but we're far, far away from that still.

You know, Java used to be the next big thing everyone was supposed to be learning but I'd say the hype has somewhat toned down and while it still has it's place no-one suggests that everyone would be using Java in a few years. It'll probably be the same with C#.[/quote]

At school, the A level computing syllabus is now moving towards Java instead of Pascal. I defied the flow and decided to use C++. It is harder for a beginner. Since the OP already knows C++, I don't know why he wants to change.

C#? I used that a bit while on Windows. Wasn't bad, quite nice to program in.

---

### Post by biguns on 2006-02-21
[QUOTE=slux]In Microsoft's dreams maybe. If you're holding your breath for the programmers to mass-migrate to C# anytime soon, don't keep holding for too long because it's not going to happen anytime soon......

.......You know, Java used to be the next big thing everyone was supposed to be learning but I'd say the hype has somewhat toned down and while it still has it's place no-one suggests that everyone would be using Java in a few years. It'll probably be the same with C#.[/QUOTE]

I can't find it but I read somewhere (mabe at [/.]("http://www.slashdot.org/")) that Microsoft has put at least 2 billions dollars in C# and this is the language most of thier coders currently use... Flash in the pan...I don't think so...but maybe.

---

### Post by xhie on 2006-02-21
We get more bloons at the ACM competitions when we use java....
it gets points for that I suppose.

---

### Post by gordyt on 2006-02-21
Howdy Leiki,

[QUOTE=Leiki]@davebradford...

Thanks for your help (as well as everyone elses)! I think I'm going to stick to Java. Nothing really to lose, since I barely know C++ in the first place. After installing the JAR file of BlueJ by using ```
java -jar bluej-212.jar
``` it says ```
Failed to load Main-Class manifest attribute from bluej-212.jar
```. How do I fix it?[/QUOTE]

I just tried installing it and that same line worked just fine.  Make sure you have a good version of Java2 installed.  Try this from your command line:

java -version

When I did that command, this was the result:
```

 java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)

```

You should probably have java 1.4.x or 1.5.x installed.

--gordy

---

