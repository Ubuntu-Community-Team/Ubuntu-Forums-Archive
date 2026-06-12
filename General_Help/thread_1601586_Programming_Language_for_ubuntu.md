---
title: "Programming Language for ubuntu"
date: 2010-10-20
forum: General Help
---

### Post by TurboThiago on 2010-10-20
I have made a program, but i've made it in visual basic 6, a programming language for windows. But I want to convert it to be used in ubuntu and share it to the community. But Visual Basic 6 doesn't work in Ubuntu. 

What's the language used in ubuntu? Java? C++? I think it can be stupid but I don't know. ](*,) 

Thanks to everybody

---

### Post by WorMzy on 2010-10-20
Python, C, C++, and Java are all well supported languages on Linux. Python and Java for obvious reasons, and there's GCC for compiling C and C++ programs.

---

### Post by TurboThiago on 2010-10-20
Is there any programming ambient for these languages? I'm starting in the world of programming and i'm not that good yet.

---

### Post by WorMzy on 2010-10-20
Well, there's Netbeans and Eclipse, which are primarily for Java, but have various add-ons for developing in other languages. There's also Anjuta, which is primarily used for developing C and C++ applications, and has an integrated GUI developer for GTK projects. PIDA is one available for Python, though I've never really used it.

---

### Post by Vectorferret on 2010-10-20
I'd go with Python or Perl if you want to get started on simple Ubuntu programs (and both can transition to more complicated programs as well). Python is probably better if your more of a science/math type where as Perl tends to be nicer for the more linguistic brains (at least that's what my programming languages prof told me). Both can also be used on Windows (usually without changing anything you've written).

---

### Post by TurboThiago on 2010-10-20
Thanks to everybody. I think i'll do it in Java using Eclipse. I have used netbeans in a course, but I did not take it serious because I was more interested in the another language of the course. Althought, I did not liked it, so I'll try eclipse. 
If I can make my program in Eclipse i'll share here in the comunnity. But, first i'll try others simple programs.
Thanks to everybody.

PS: sorry to my bad english, I from Brasil and there is a long time that i don't train my english.

---

### Post by 7h3d4rk0n3 on 2010-10-20
Best bet is Java, as it is OS independent.

---

### Post by alexfish on 2010-10-20
Hi

the nearest to Visualbasic 6 is Gambas , Ideal if you want a relaxed transition but for redistribution requires Gambas runtimes 

also some Visualbasic 6 exec's will run under wine

as a transition to another language 

look up Monkey studio ( based on QT ,  syntax languages,  python and more)

also look up Quickly - Ubuntu (based on python with glade interface designer)

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

---

### Post by GregBrannon on 2010-10-20
Check out the stickies and other threads of interest in the Programming Talk sub-forum for other advice, links to tutorials, and general programming help.  Come back and ask questions there if you need programming help.

Good luck!

---

### Post by Mr.Sykkoh on 2010-10-20
You could also take a look at the mono project
[http://www.mono-project.com/Main_Page]("http://www.mono-project.com/Main_Page")

I personally prefer Java but check out mono

---

### Post by directhex on 2010-10-20
Gambas is close to VB6 syntax. There's also VB.NET via Mono.

---

### Post by allium culpa on 2010-10-21
If I may, I'd like to throw in C++ as a suggestion. I used VB6 when I was just beginning, too, but I quickly "grew out" of it. As I grew as a programmer I started to see it as inflexible and buggy, and I had to cope with the fact that it was platform-dependent (around the same time I was discovering linux!).

Right away I fell in love with C++. The syntax is quite similar to java; you might consider looking into the differences between the two. But there are lots of languages to choose from! Ubuntu and all its programs aren't written in any one language. C, C++, perl, java, pascal, ruby, lua, the list goes on-- and I can't believe no one has mentioned RealBasic (a variant of BASIC designed to be more platform-independent than Visual Basic), but I've personally never tried it. Whichever you pick, it can be helpful to aim for a cross-platform IDE (Eclipse or Netbeans for Java, Code::Blocks for C++; there are many others) if you'd like to do your coding on both Linux and Windows, so you can don't have to learn to navigate two different IDE's.

Finally (and I don't know how new you are to programming, so I'll tell you just in case), it can be kind of a shocker to go from progamming in VB6 to programming in a language like Java or C++. You're probably used to both writing the code and designing the graphical interface for your programs inside the VB6 IDE at the same time. GUI programming in other languages is usually *much* more involved, -especially- if you want to write cross-platform apps. There are toolkits for doing so, but they tend to require a greater understanding of a programming language and programming in general, so you may want to stick to writing command line applications in your new language of choice until you're very comfortable with it before moving on to GUI-programming.

In summary, my suggestions:
[LIST]
[*]Choose a programming language you think you'll like (I personally recommend C++; someone else recommended perl, which I am also fond of)
[*]Choose an IDE to develop in, preferably a cross-platform IDE *if* you want to code on linux *and* windows, and make sure you have a compiler if it's not a scripted language (you probably won't have to worry about this if you pick a popular language like C++, you'll almost certainly already have the GCC compiler on Ubuntu)
[*]Find and follow some great tutorials on your programming language of choice, and become very comfortable with writing command-line applications for it before moving on to GUI programming. *Don't* be discouraged if it seems too hard at first, or if you wanted to jump right into writing GUI applications-- command line programs are *still very useful, _especially_ in linux!*
[*]Share your work, and explore other people's programs; learn and grow like this, it is at the very core of the ubuntu philoposhy. If you don't, you'll be missing out on the best part of linux programming.
[*]Be proud of all your work, no matter how small or silly, even the first hello-world :)
[*]Repeat the learning process for GUI applications. I highly recommend rewriting old VB6 programs when you get to that point. You'll be *amazed* at how much you've grown as a programmer when you do (I have very old programs I've rewritten from top to bottom 4 or 5 or more times!)
[/LIST]

Sorry I've rambled on a bit much. I know you asked for suggestions for a programming language to choose, not for advice, but I think it's important to know what to expect if you follow up on any one the suggestions offered in this thread. You should research and experiment until you find the language for you, but don't rely on your very first impression, because choosing a new language can sometimes be a daunting task.

I hope I've been of some help. I've over-simplified several things, so there's a lot more to say but I don't want to hijack the thread. ;) Good luck! This can be a very exciting experience if you're positive about it. :)

---

### Post by Narendran95 on 2010-11-02
Please! I really need help in GAMBAS. I want to make a program that simulates mouse click. Please help... URGENT!

---

