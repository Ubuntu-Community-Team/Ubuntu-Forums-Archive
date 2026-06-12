---
title: "allegro and basic c++ game programming build error"
date: 2010-11-30
forum: General Help
---

### Post by Bezique on 2010-11-30
Hi All,
Not sure if there is a more appropriate subforum to place this question in.

I am running ubuntu 10.10 - installed last week.
I am trying to set myself up to do cpp programming.

I have Geany installed and necessary g++ libraries etc. I have been using them successfully. I have installed the allegro game programming library:

sudo apt-get install aptitude
sudo aptitude install liballegro4.2-dev

(I required aptitude first)

I have linked this to Geany via:

**Compile:** 
g++ -O0 -g3 -Wall -c -o"%e.o" "%f" 
**Build:** 
g++ -o"%e" ./%e.o `allegro-config --libs --static` 
**Execute:** 
"./%e" 

As a test I have taken an ope-nsource cpp game code (tictactoe) from here:
[http://www.cppgameprogramming.com/cgi/nav.cgi?page=tictactoe](http://www.cppgameprogramming.com/cgi/nav.cgi?page=tictactoe)

When compiling I get no errors however the build tells me:
make: *** No targets specified and no makefile found. Stop.

Having searched forums I understand that this means that the make file is missing or has not passed through ./configure.

I was of the impression that the above linked tictactoe game was so small that it does not need an independent make file.

Am I missing necessary files to compile the game or have I made an error in my configuration of allegro?

Thanks for your help,

-- Bez

---

### Post by burton247 on 2010-11-30
Have you tried compiling and linking via the terminal and not through Geany. I've seen people get this error before. Think it may have been that g++ wasn't installed. It was through eclipse though, give it a go at compiling in the terminal though

---

### Post by Bezique on 2010-11-30
Thanks for the suggestion.

Prior to your posting I was reorganising my file structure. I placed my tictactoe.cpp file inot a new dedicated subdirectory and geany began to work. Your method works also.

I have not been able to identify what was causing the problem.

In case anybody else takes an interest in the linked tictactoe game. After correcting for the above I got this compilation error message:

/usr/bin/ld: Warning: alignment 4 of symbol `y' in ./tictactoe.o is smaller than 16 in /usr/lib/liballeg.a(imisc.o)

I quick web search shows that it is related to the number of bytes given to 'y' in the .cpp code. I do not understand the inns and outs, but was able to eliminate the error by redefining 'y' as a double. I doubt this is a good practice solution to the problem.

---

