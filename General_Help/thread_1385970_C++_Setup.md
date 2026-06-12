---
title: "C++ Setup"
date: 2010-01-20
forum: General Help
---

### Post by TheGreenFox on 2010-01-20
Hello,

I am taking some collage programing classes which are using C++. I would like to setup every thing up on my ubuntu box. 

Here is what I have to work with,
1. I am using a Dell Mini 10 netbook so not a lot of processing power
2. I am fairly sure that I will need to submit completed programs to my professor who I am assuming is using windows
3. I have been using ubuntu sense 8.04 so I am competent in its use

I am not sure if this is even possible or practical.

Thanks in advance,
GreenFox

---

### Post by i.r.id10t on 2010-01-20
If you are doing ANSI standard C/C++ then you can just use gcc - apt-get install build-essential gets your compiler, etc.

If you are taking a C# or .net class, then you'll need windows and visual studio.

I'd ask your instructor if you can use GCC.

---

### Post by muteXe on 2010-01-20
If he/she is teaching you **100% ansi** C++, then whatever you write and compile on your linux box using gcc will also compile on his/her windows machine.

---

### Post by Lars Noodén on 2010-01-20
> **TheGreenFox said:**
> Hello,

I am taking some collage programing classes which are using C++. I would like to setup every thing up on my ubuntu box. 

Here is what I have to work with,
1. I am using a Dell Mini 10 netbook so not a lot of processing power


That's plenty for any course.

> **TheGreenFox said:**
> 
2. I am fairly sure that I will need to submit completed programs to my professor who I am assuming is using windows


Hey.  No need to be casting aspersions against the competency and character of your faculty.

Some of your classmates, however, might benefit from instructions like these:
[http://www.claremontmckenna.edu/math/ALee/g++/g++.html](http://www.claremontmckenna.edu/math/ALee/g++/g++.html)
Here is another set of instructions:
[http://www.icce.rug.nl/edu/1/setup.shtml](http://www.icce.rug.nl/edu/1/setup.shtml)

But really they'd be much better off working in a proper development environment and should, if they still have Windows, at least dual boot into Linux for programming. 

> **TheGreenFox said:**
> 
3. I have been using ubuntu sense 8.04 so I am competent in its use

I am not sure if this is even possible or practical.


Linux and other unix-like platforms are the norm for computer science, software engineering and a lot of other development.  GCC is probably the best compiler available currently.  

[http://wiki.kruel.org/index.php/Intro_to_C_Plus_Plus](http://wiki.kruel.org/index.php/Intro_to_C_Plus_Plus)

But there are a lot of tutorials for more advanced work.
[http://www.cuil.com/search?q=g%2B%2B+linux+tutorial](http://www.cuil.com/search?q=g%2B%2B+linux+tutorial)

The basic C++ compiler is provided in Ubuntu by the package [g++](http://packages.ubuntu.com/karmic/g++).  

For editors, at the beginning I have seen best results with Kate or Geany.  Both provide a nice little window to test your code in, I myself prefer Kate.

---

### Post by Simian Man on 2010-01-20
> **i.r.id10t said:**
> If you are taking a C# or .net class, then you'll need windows and visual studio.
You can program in C# with Mono.  In fact, since the C# language has fewer dark corners than C++ does, you would actually probably be *safer* using C# on Linux than C++.

> **muteXe said:**
> If he/she is teaching you **100% ansi** C++, then whatever you write and compile on your linux box using gcc will also compile on his/her windows machine.
That's generally true, but there are some areas to watch out for.  First make sure you turn off gcc extensions with the -pedantic flag.  Also use -W -Wall to turn on all warnings just to be safe.  An example where this can bite you is that GCC accepts variable length arrays while Visual C++ does not.

In general though, there are more gotchas going from Windows to Linux, so you should probably be OK with the flags I mentioned.

> **Lars Noodén said:**
> But really they'd be much better off working in a proper development environment and should, if they still have Windows, at least dual boot into Linux for programming. 

Linux and other unix-like platforms are the norm for computer science, software engineering and a lot of other development.  GCC is probably the best compiler available currently.  

There is nothing wrong with programming in the Windows environment.  I prefer the way Linux does things in a few areas, and it is prevalent for academics like me, but it isn't true that *nix is the norm for software engineering in general.  You will find more software developers using Microsoft tools than GCC I'm sure.

The area where Visual Studio really wins is the debugger.  It blows gdb out of the water honestly.

I would just ask the teacher honestly.  It could be that he is into Linux too and will have no problem with you using it.  Worst comes to worst, I'm sure there is a computer lab somewhere where you can test your code before handing it in.

---

### Post by TheGreenFox on 2010-01-20
Thanks for the quick reply's. 

> 
[QUOTE]Quote:
Originally Posted by TheGreenFox View Post
2. I am fairly sure that I will need to submit completed programs to my professor who I am assuming is using windows
Hey. No need to be casting aspersions against the competency and character of your faculty.
[/QUOTE]

Your right I shouldn't judge until I know.

Love this forum,:P

---

### Post by Lars Noodén on 2010-01-20
> **Simian Man said:**
> You can program in ... with ...


Except that the question is about learning C++ and not about replacing Java.  

> **Simian Man said:**
> 
There is nothing wrong with programming in the Windows environment. 

Unless there students are there to learn good habits and proper programming technique.  The Window tools lock students into bad habits and poor design that can take years or decades to unlearn.  Then there is always the issue of whether it is right to encourage beginners to become dependent on technology locked into a single platform.  Or whether its right to help grow income used to subsidize poor technologies and practices.  

Or, speaking of practices, unless the business practices, legal history, and company ethics come into consideration.  

OS X, technically, legally, ethically would be a better runner up if you can't develop on Linux.  

@ TheGreenFox  : you might ask also over on the [education and science](http://ubuntuforums.org/forumdisplay.php?f=169) where you'll find more computer science or programming teachers.  

As mentioned above, either editor, Kate or Geany, plus g++ will give you an intro to what's used in industry.  

For what it's worth most mobile applications are built using C++ and working on Linux or OS X will give you an easier transition to Android, Maemo or iPhone.  [Qt](http://packages.ubuntu.com/karmic/qt4-demos) will give you a good collection of tools to use to make nice graphical interfaces for your C++ programs.  But that would necessarily be for your first term.

---

### Post by Simian Man on 2010-01-20
> **Lars Noodén said:**
> Except that the question is about learning C++ and not about replacing Java.
Yes, but the person I was quoting made the untrue claim that you need Windows and Visual Studio to develop in C#.

> **Lars Noodén said:**
> Unless there students are there to learn good habits and proper programming technique.  The Window tools lock students into bad habits and poor design that can take years or decades to unlearn.
WTF are you talking about?  I can't think of a single way that the Windows tools lend themselves to poor practices or design.

> **Lars Noodén said:**
> Then there is always the issue of whether it is right to encourage beginners to become dependent on technology locked into a single platform.
If you stick to standardized languages and cross-platform libraries, there is exactly nothing about developing on or for Windows that locks you in to that platform.

> **Lars Noodén said:**
> Or whether its right to help grow income used to subsidize poor technologies and practices.

Or, speaking of practices, unless the business practices, legal history, and company ethics come into consideration.  

OS X, technically, legally, ethically would be a better runner up if you can't develop on Linux.
What does this have to do with anything?  Are you arguing that it's somehow immoral to develop software on or for Windows?

> **Lars Noodén said:**
> As mentioned above, either editor, Kate or Geany, plus g++ will give you an intro to what's used in industry.
Yeah, of course most programmers in the industry use g++ with a basic text editor :rolleyes:.


> **Lars Noodén said:**
> For what it's worth most mobile applications are built using C++ and working on Linux or OS X will give you an easier transition to Android, Maemo or iPhone.

Actually those are pretty horrible examples.  Android is Java-based and can be developed under any operating system - I suspect most use Windows.  And the iPhone is developed with Objective-C on OSX.  Only Maemo is really developed with Linux development in mind.  And mobile applications aren't the whole of software development either.

---

### Post by Lars Noodén on 2010-01-21
> **Simian Man said:**
> 
Yeah, of course most programmers in the industry use g++ with a basic text editor .

g++ **is** the most commonly used c++ compiler.  

The original question was about an **intro** to c++.  There the answer is a basic text editor **with** some basic IDE functions:  kate and geany

If the question had been about getting a professional grade IDE, then the answer would have been Eclipse, Netbeans, Kdevelop or even Emacs.  However, those are most useful when the skill level has come up to the point where basic programming skills are well established and the programmer is starting to work with very large modules with many functions and classes to track.

He instead got hit by noisy MS trolls.  

Back to geany and kate.

Here is a nice article about [using Geany as an IDE](http://www.ubuntunews.info/geany-perfect-programming-ide).  For **introductory** programming courses, it is perfect.  [kate](http://kate-editor.org/kate) also is a basic text editor **with** basic ide capabilities.  

From the Geany article:
[indent]*"Geany does almost everything I need. The only feature I'd like to see is editing remote files (via SSH)*[/indent]

Guess what, using SSHFS it is possible to edit remote files, too.  

Having a simple, clean interface like those provided by kate and geany is essential when introducing programming.  The most elementary IDE functions are there, too, like syntax highlighting.

---

### Post by TheGreenFox on 2010-01-21
Thanks, Geany is just what I am looking for. 
@Lars Noodén did not know where to post it, now I do :)

---

### Post by Lars Noodén on 2010-01-21
> **TheGreenFox said:**
> Thanks, Geany is just what I am looking for. 
@Lars Noodén did not know where to post it, now I do :)

In addition to the education section, there is also a section dedicated to  [programming](http://ubuntuforums.org/forumdisplay.php?f=39) on Ubuntu.

---

