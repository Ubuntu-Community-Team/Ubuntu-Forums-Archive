---
title: "what is needed to program on GNU/Linux"
date: 2011-12-19
forum: General Help
---

### Post by davethewave83 on 2011-12-19
what would I need in order to code from within Ubuntu? Is there any specific language (C/+/++/#, Delphi, Python, VB)? or would any language work? A specific IDE that everyone likes perhaps? 

Thanks for any and all support guys.

---

### Post by ReptilianShadow on 2011-12-19
I won't get into the "best language", but as far as "will it work", I'm pretty sure VB doesn't work on Linux.

C(++/#) all work on linux, for C and C++ look into gcc [http://gcc.gnu.org/]("http://gcc.gnu.org/").
Also, (gcc should be preinstalled, but I'm not sure) you can use:
```
man gcc
```
in terminal for additional usage info.

C#, The Mono Project should cover that. [http://www.mono-project.com/CSharp_Compiler]("http://www.mono-project.com/CSharp_Compiler")

For Delphi, I came up with something called Kylix. See what you can find off that.

Python works fine, including their "built-in" IDE in terminal/bash.

Java!

As for IDEs, I'd strongly recommend Eclipse if you haven't already heard of it. You can get it for linux on their website[http://www.eclipse.org/downloads/]("http://www.eclipse.org/downloads/")
Eclipse is primarily for Java development but there is also a version for C and C++.

I know you can install at least the Java version of Eclipse via the Ubuntu Software Center if you prefer that method.

More programming language support than that, but I'll stick to your list.

I'm really not an expert with programming languages. So, sorry if I'm not giving you the depth of info you're looking for.

---

### Post by QIII on 2011-12-19
Mono *used  *to be the way to go with C#.  But that .NET  implementation for Linux seems to be dead.  Novell pretty much abandoned  it due to lack of interest.  It has been spun off to a company called Xamarin.  We'll see if life is breathed back in to it.
 
.NET is not native to Linux, so don't get your hopes up for C# or VB.NET.  VB6 is a plain no-go on Linux.

C, C++, Python, and many more are all well at home on Linux -- and make up much of Linux or its desktop environments.

As far as IDEs you have a treasure trove.  I can't tell you how many of these are worth a hill of beans.  I use NetBeans, KDevelop and Eclipse:

[http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)

Most of what you need for building and compiling is found in the build-essential package.

---

### Post by killermist on 2011-12-20
A lot of the choice of programming language is affected by what you're looking to do.
Basic scripting (which is what I do most often) is done best/easiest with:
bash, perl, ruby, python, and possibly php (thought not often for things not web-related)
Web scripting/programming is generally done with php, perl, and javascript, but there are lots of other options too.
As to larger programs/applications, I don't even know where to begin, but I know that a LOT of stuff is written in C/C++ (and rightly so) because it gives a lot of flexibility in how far down the rabbit hole you want to go to tweak performance/optimization.
Some programs appear to be done as compiled python, which is capable of some good speed.

I personally have had very little luck with Java (horrible speed inefficiency), as have many others, and so many users will shy away from Java based programs (like Azureus has been trying to contend with for years). 
Mono and C#, in being/using a .NET framework (as something started originally by Microsoft, even if made more sane/open since then) leaves a bad taste in some people's mouth, and so they'll shy away from programs using .NET (free and sane, or not).


[note]
I'm not trying to start any arguments as to the merit or lack of any particular language(s), just trying to offer some perspective.

---

### Post by Mark Phelps on 2011-12-20
> **davethewave83 said:**
> what would I need in order to code from within Ubuntu? 

The detailed answer depends on WHY you want to code, or put another way, what your intended runtime target happens to be.

IF you just want to write FOSS stuff for the open source community, then Linux is a good platform for doing that.

If, instead, you intend to write stuff for the Windows community, meaning it's going to make extensive use of .NET, Silverlight, DirectX, and others Windows components, then Ubuntu is a poor choice because, you will need a Native Windows environment to test your code to confirm it actually works properly in Windows.

---

### Post by directhex on 2011-12-21
> **QIII said:**
> Mono *used  *to be the way to go with C#.  But that .NET  implementation for Linux seems to be dead.

This is far from accurate.

---

### Post by davethewave83 on 2012-01-22
Thank you all for your answers! I've coded a little bit in the past, but never really got very involved with programming. I just wanted to know where to start, so that I can experiment and see if I can code any better than I used to and to see what I can learn.

---

