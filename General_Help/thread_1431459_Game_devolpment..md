---
title: "Game devolpment."
date: 2010-03-16
forum: General Help
---

### Post by nlvldg on 2010-03-16
I want to program a 16-bit sprite-based JRPG video game. What programs are available that could help me in this. I have practically no experience with this programming but, I figure if I'm going to learn it, better start big.

---

### Post by wwsoft on 2010-03-16
"better start big" you could not be more wrong. You'll eventually figure out that Starting small is the best [and only way] or creating games. Anyways if you dont know how to program your in for a bumpy ride. 

I used [game maker]("http://www.yoyogames.com/make") a few years ago but its only for mac and windows.  

if your not going to use a high level gui and you want to program your going to need to select a language to lean. Heres a few:


[LIST=1]
[*][C / C++]("http://www.learncpp.com/")
[LIST=1]
[*]Pro: Fast , Industry Standard.
[*]Con: Must be compiled for different OS's , Debuging
[/LIST]
 
[*][Python]("http://python.org")
[LIST=1]
[*]Pro: System Independent , easier to learn
[*]Con: Slow
[/LIST]
 
[*][Java]("http://www.java2s.com/Tutorial/Java/CatalogJava.htm")
[LIST=1]
[*]Pro: System Independent , Fast[er] than python
[*]Con: As hard to lean as C/C++ (its based off of it , python is too just not as much)
[/LIST]
 
[/LIST]
note: recommended IDE for C/C++ [Code::Blocks]("http://www.codeblocks.org/")

After you learn the basics of whatever language you chose you need to find a game programming library or engine. I use [SDL]("http://libsdl.org") for my games , it supports use for 2d and 3d games (using opengl). Its cross platform and it supports many programming languages.

After that you learn the basics of the language and the library with [tutorials]("http://www.lazyfoo.net/SDL_tutorials/index.php")  (<-  lazyfoo ), examples and [even more tutorials]("http://www.libsdl.org/tutorials.php") (<- Sdl tutorial listing). you can start making cheesy pong and space invader games.

After you get more experienced you can start making cool [Good looking , Good Playing] games not just text based adventures or some old pong cone but like your RPG you mentioned. 

it takes time to lean but eventual you'll create something good if you keep trying ;)

Please note: The best game designers are not programmers because they do not know any limitations learned in programming

---

### Post by kostkon on 2010-03-16
A nice and fun (and easy, why not) way to do it would be to learn some Python (it's a nice language, that you can later use for other projects) and use [*pygame*]("http://www.pygame.org/").

---

### Post by J V on 2010-03-16
python is only 14 times slower than C... but its 400 times faster than bad C...

Good programming beats the language hands down, go for whatever is easiest to use... Pythons only downside is that it can't be compiled, so I would go for C# 4.0 (mono) as it has dynamic typing and garbage collection, and can be compiled...

---

### Post by wwsoft on 2010-03-16
Good luck which ever way you go. But in the long run C++ beats them all hands down :p !

---

### Post by falconindy on 2010-03-16
This is going to get religious, but I can't resist:

Java: Easy to learn and write, but has some unreasonably poor design choices. Also, learning the object oriented orgasm that is Java before anything else can be harmful to one's learning. Understanding and being competent with multiple paradigms is vital to being a successful programmer.

C++: See interview [here](http://harmful.cat-v.org/software/c++/I_did_it_for_you_all) with C++'s creator, Bjarne Stroustrup. Nuff said.

C#: I would never in a hundred years recommend a MS based programming language to anyone. They're poisonous enough on their own. Don't help them propagate, let alone propagate a language based on C++.

C: The one true religion. Obviously not optimal for all circumstances. Got some heavy number crunching to do? Need a fast app for an embedded platform? Look no further.

Python: Fantastic starter language. Offers multiple paradigms, freedom from compiler-related hangups, and still runs fast enough for day to day stomping around. Infinitely extensible through a vast collection of libraries. Unfortunately, this teaches you a lot about how to import libraries and little about how to write your own efficient and reusable code.

---

### Post by soltanis on 2010-03-16
This looks like a discussion better answered on the programming forums (from the top-level screen, the second category of forums, on the bottom left).

I'll suggest you start small, like someone else said, and learn the basics of programming before you try to code up something real.

A great starter language is **Python**. It will expose you to programming concepts without beating you over the head with:

Machine semantics (C),
A single paradigm that works great in some cases and sucks for all the others (Java),
An overly complicated language with too much baggage and no clear direction (C++),
Out of hand syntax (Perl).

It comes pre-installed on Ubuntu. Pop open a terminal and type "python", then open up the browser and follow along with a beginner's tutorial.

EDIT:
Try this one out
[http://www.sthurlow.com/python/](http://www.sthurlow.com/python/)

You can skip the lesson on "Installing python".

---

### Post by Letrazzrot on 2010-03-16
Here's my humble opinion, do with it what you will:

Your best choice (IMO) would probably be Python, since it seems fairly well integrated with Linux, and is often termed a 'beginner language.'  There seem to be many python bindings for various game/graphics/sound libraries out there, too.  (Note:  I am not familiar with Python... yet).

Next choice would be C# or Java.  My personnel preference is C#, but I can't think of any technical reasons for choosing one over the other (at least, for someone just starting out).

For an absolute beginner, I couldn't in good conscience recommend C or C++.  Especially the latter.  Unmanaged environments (where you have to control all those pesky memory issues) are ill-suited to beginners (or, for that matter, an expert who doesn't have other considerations).  C++ is something I keep locked in the closet, and only pull it out in the darkest hours of the night to experiment on :P

Of course, your choice would also depend on the amount of tutorials, guides, and books you can find on the subject.  You will need to start collecting these.

But yeah, as others said, start small.  Very small.  Programming is a never-ending process of learning, and trying to take on too large of a project leads to frustration and vaporware.

I know, because I am a king of vaporware ;)

Good luck!

[EDIT] p.s.:  oh yeah, and I wouldn't let execution speed be a factor in deciding, at least not for a very, very long time to come.  Unless you are targeting a system with ridiculous constraints, I'm sure any modern language/environment will be plenty fast.

---

### Post by wwsoft on 2010-03-16
@Letrazzrot

your right about C. I have been programming for way to long. To recommend C right off the bat would be killing off some really enthusiast game developers.

@nlvldg

 Python is much simpler (as seen below)

Python - Print Hello World

```

# Hello World
# no imports

    print "Hello World"


```C++ - Print Hello world

```

#include <iostream>

using namespace std;

int main()
{
        cout << "Hello World" << endl;
        return 0;
}

```(As Said Before) Good Luck Future Game Developer :) 


[LIST]
[*]The Offical [URL="http://docs.python.org/tutorial/index.html"]Python Tutorial 
[/URL]
[*][Pygame]("http://www.pygame.org/news.html")
[*][Pygame Tutorial Listing]("http://www.pygame.org/docs/")
[/LIST]
 
@Letrazzrot [again]

if your the king of vaporware I must be the chieftain of long lost Vapor Island :)

---

### Post by janjust on 2010-03-17
I'm just going to throw out that the interview link is a bogus interview.
There are many reasons not to use C++ , that link isn't one of them.

[link]("http://www2.research.att.com/~bs/ieee_interview.html")

---

### Post by drreed on 2010-04-06
> **kostkon said:**
> A nice and fun (and easy, why not) way to do it would be to learn some Python (it's a nice language, that you can later use for other projects) and use [*pygame*]("http://www.pygame.org/").

According to that link, pygame has been rewritten in javascript, and they're hoping everyone upgrades all their code to js, because as they put it "it's way better than python".

lol

:guitar:

---

