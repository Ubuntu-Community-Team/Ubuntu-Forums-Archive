---
title: "C++ writing program"
date: 2006-06-12
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-12
I'm new to writing code but I was wondering if there are any for linux that I could use to make a program. I tried Just Basic, but it starts up, then closes becaus it's for microsoft. :cool:

---

### Post by IYY on 2006-06-12
All you need is the compiler and a text editor. 

g++ myprogram.ccp

---

### Post by s_h_a_d_o_w_s on 2006-06-12
Which compiler do you reccomend?

---

### Post by syxbit on 2006-06-12
g++ is the compiler
you can code in gedit, and then compile in the terminal with g++
i think g++ comes default on ubuntu, if not, you can just install it
sudo aptitude install g++
then you can just type the command on the terminal ("man g++" for info about doing that)
hope that helps

---

### Post by ErezNoodle on 2006-06-12
I use gcc, you can just apt-get it.

---

### Post by s_h_a_d_o_w_s on 2006-06-12
Do I need the code to be in a certain format?

---

### Post by taurus on 2006-06-12
Certain format!!!  The code is just a regular text file so you can do whatever you want with it and use whichever text editor you want as long as the syntax is correct.  Make sure you install build-essential as
```

sudo apt-get install build-essential

```

---

### Post by jaymode on 2006-06-12
If you are looking for an IDE(Integrated Development Environment) look into Anjuta and Eclipse. Eclipse is very good for java, for me it was a little slow when trying to do C++ in it. Anjuta was not bad. GCC is also good, but not as "nice". In fact GCC is used by Anjuta and Eclipse to compile c++ code if i remember correctly.

---

### Post by solarwind on 2006-06-12
[QUOTE=jaymode]If you are looking for an IDE(Integrated Development Environment) look into Anjuta and Eclipse. Eclipse is very good for java, for me it was a little slow when trying to do C++ in it. Anjuta was not bad. GCC is also good, but not as "nice". In fact GCC is used by Anjuta and Eclipse to compile c++ code if i remember correctly.[/QUOTE]


Well, in my opinion, KDevelop is the best ide for linux. Use Synaptic to get KDevelop.

It's really easy to use as well!

---

### Post by dudus on 2006-06-12
[QUOTE=jaymode]If you are looking for an IDE(Integrated Development Environment) look into Anjuta and Eclipse. Eclipse is very good for java, for me it was a little slow when trying to do C++ in it. Anjuta was not bad. GCC is also good, but not as "nice". In fact GCC is used by Anjuta and Eclipse to compile c++ code if i remember correctly.[/QUOTE]
I migth be teribily wrong but I think gcc is for plain C and g++ is for C++. But both are the same program! Just different names with differents pre-flags set

---

### Post by Xilon on 2006-06-13
yeah it's the same compiler although if you try compiling a c++ program with gcc you get errors for some reason :S
you can issue a command like ```
gcc -x c++ -o program program.cpp
```(the -x c++ isn't actually necessary since GCC picks up on teh file extension anyway)
which should be the equivalent to ```
g++ -o program program.cpp
``` but gcc gives weird errors and g++ compiles correctly... **on the same file!**
Maybe I'm just doing it wrong... Or maybe it's because GCC and G++ use different library paths? because the errors mainly whine about the functions not being defined.

Anyway for c++ programs just use G++ in the terminal, it's the easiest way to do it, and definitely the fastest :) If you're a beginner programmer then you won't have a GUI program anyway, just console stuff.

---

