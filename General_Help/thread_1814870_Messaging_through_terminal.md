---
title: "Messaging through terminal"
date: 2011-07-30
forum: General Help
---

### Post by devinsoles on 2011-07-30
Hi again everyone! My friend brought up this cool idea to me about messaging through your cmd/terminal. Problem is that he isnt on the same internet connection as me, and the only guides I can find online are for people on your same network. I was wondering, if Im on my laptop, is their anyway to message my friend through command prompt on his home computer? Weve been trying to figure it out with no luck. I really appreciate any help that can be given!

---

### Post by pqwoerituytrueiwoq on 2011-07-30
possibly with port forwarding enabled on the right port
anything wrong with a instant messenger?

---

### Post by devinsoles on 2011-07-30
Well of course not, and txting works fine as well. We are just wanting to learn some new tricks with our terminals. Im new to linux and just trying to experiment with the various things you can do with code ya know?

---

### Post by mcduck on 2011-07-30
The Pidgin project has a terminal-based instant messaging application, Finch, which supports all the same protocols Pidgin, Empathy and other libpurple-based IM apps do.

Finch should be available in Ubuntu's repositories. :)

edit: Here's a guide to using Finch (just ignore the part about installing it and get it through the package manager instead):
[http://tuxarena.blogspot.com/2010/09/guide-to-using-finch-terminal-based.html]("http://tuxarena.blogspot.com/2010/09/guide-to-using-finch-terminal-based.html")

---

### Post by devinsoles on 2011-07-30
I appreciate it! but what Im really looking for is typing in a command to do so..like how you can type ipconfig to check your ip adress and such. and you can type net share and blah blah.  Typing out code to do so instead of using a program. lol.

---

### Post by whitethorn on 2011-07-30
Just adding another suggestion. I'm guessing you want to try to use the write command. To get this to work over the internet you need to do a couple things.

1) Get SSH up and running.
2) Port forwards from router to your computer so that you can ssh from outside your network onto your computer
3) Create a new user for you fried to log in as.
4) Friend ssh's onto your computer (or you onto his), uses write to post a message to your terminal

This is usually a waste of time over the internet and of course he needs a user account on your computer.

---

### Post by haqking on 2011-07-30
> **devinsoles said:**
> I appreciate it! but what Im really looking for is typing in a command to do so..like how you can type ipconfig to check your ip adress and such. and you can type net share and blah blah.  Typing out code to do so instead of using a program. lol.


code is a term given to programming as in programming code.

ipconfig is not code, it is a command.

there are commands for sending messages from terminal such as the write command.

man write

for more information

however these are for users on the same system or network.

They could be issued to a remote network via vpn connection but not through a general internet connection.

---

### Post by devinsoles on 2011-07-30
Oh my apology! See, Im new to all of it :P.

---

### Post by haqking on 2011-07-30
> **devinsoles said:**
> Oh my apology! See, Im new to all of it :P.

no worries, you are in the right place to learn ;-)

---

### Post by devinsoles on 2011-07-30
Well you guys definitely know what your talking about! Jw, I know programming takes a long time to learn, but do you know of anywhere I could start learning?

---

### Post by hakermania on 2011-07-30
You're again on the right place. Just let us know what are your needs, what would you like to program to tell you your IDE and programming language that depicts your needs.
You had better make a new thread here: [PT]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by devinsoles on 2011-07-30
Guidance is appreciated greatly! See, I dont even know exactly what capabilities programming has. What all you can do with it, so I dont even know where to start lol.

---

### Post by hakermania on 2011-07-30
> **devinsoles said:**
> Guidance is appreciated greatly! See, I dont even know exactly what capabilities programming has. What all you can do with it, so I dont even know where to start lol.

Just think that whatever you use on your PC, mobile device or Ipod is programmed through a programming language :)
So it has lots of capabilities, but you have to choose your programming language, for example, Python is better than C++ as for networking but it is a Script language and is much slower, on the other hand Perl is Script and very good at text processing etc...
So, you should thing about what you'd like to make yourself and step by step reach a level and make a usable application.

But if you want my personal opinion you could start by a scripting language, like BASH and then go for something more High-Leveled like C++
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by zero2xiii on 2011-07-30
> Just think that whatever you use on your PC, mobile device or Ipod is programmed through a programming language 
So it has lots of capabilities, but you have to choose your programming language, for example, Python is better than C++ as for networking but it is a Script language and is much slower, on the other hand Perl is Script and very good at text processing etc...
So, you should thing about what you'd like to make yourself and step by step reach a level and make a usable application.

Very true,

Bash is easy and scary powerfull if you combine it with simple command line programs (eg html2txt)..

For cross platform I would suggest C (C++ and C# included) or Java. This gives you the wides choice of platforms you can code for in a single language.

As stated, you need to know WHAT you wan to be able to do, but I find Java powerfull enough and fast enough for your more general applications, yet very simple. The awsum part is it can also be website incorporated and so forth.

C has very good GUI design tools, where as I haven't come across any GUI designers for Java just yet, haven't searched that hard to be honest, but coding it by hand isn't that hard either.

Google some example code of a few languages, and use wikipedia. Find something that fits your style and the functionality you desire. But remember, there is NO "perfect" language. But most of the time when you become more skilled, and start thinking outside the box, you can find methods to do things, the language cannot genetically do.

Play, and enjoy the learning curve :biggrin:

---

