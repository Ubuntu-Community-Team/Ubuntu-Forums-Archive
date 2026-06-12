---
title: "How to run a C program"
date: 2010-12-04
forum: General Help
---

### Post by Shinonuma on 2010-12-04
Hi,

I actually got two questions, first of all how do you run a C program in ubuntu (using gedit)? 

Second question is in VirtualBox using ubuntu, how can you change the resolution, because when I make it full screen there is a thick black line around it.

---

### Post by smo0th on 2010-12-04
by running a C program do you mean compile&run? 

to run a program you need to be sure it is executable so you do a chmod +x yourCprog and then you run it by doing a ./yourCprog

not using vbox at this time sorry on that one

---

### Post by krishnandu.sarkar on 2010-12-04
> **Shinonuma said:**
> Hi,

I actually got two questions, first of all how do you run a C program in ubuntu (using gedit)? 



Say your C program is in helloworld.c

Now do
gcc -o helloworld helloworld.c #compiles the program
./helloworld #runs the program

--OR--

gcc helloworld.c
./a.out

---

### Post by 0949er on 2010-12-04
> **krishnandu.sarkar said:**
> Say your C program is in helloworld.c

Now do
gcc -o helloworld helloworld.c #compiles the program
./helloworld #runs the program

--OR--

gcc helloworld.c
./a.out

and just in case you mean c++, install the "g++" compiler (maybe installed by default?) and do the same thing, only save your files as .cpp (doesnt really even matter) and run:

```

g++ -o program_name source_file.cpp
./program_name

```

---

### Post by Shinonuma on 2010-12-04
I'm really new to ubuntu, where do you type that? :lolflag:

---

### Post by smo0th on 2010-12-04
Applications>Accesories>Terminal

---

### Post by krishnandu.sarkar on 2010-12-05
> **Shinonuma said:**
> I'm really new to ubuntu, where do you type that? :lolflag:

If you're used to IDE, then there are many IDE's, Look at : [http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

But I(and many users would) strongly recommend to use Gedit, and compiling through terminal, that'll help you learning many things which is hidden in Windows(by default).

---

