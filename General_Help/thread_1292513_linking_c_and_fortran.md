---
title: "linking c and fortran"
date: 2009-10-15
forum: General Help
---

### Post by ubun_tut on 2009-10-15
hi,

i have been running a program written in fortran (compiled with gfortran) from the terminal, with a syntax like this

./program < input_file

now, i am writing a program in c, and this program (say, i call it CP) needs to call and execute this fortran program (FP), and take its output for further processing. 

is there a way to sort of link FP to CP? could i maybe write the CP such that it actually calls the FP from the command line? or is there some other easier way?

thx.

---

### Post by eric3_14159 on 2009-11-09
There are a few ways, with varying difficulty.

CP can call FP as if from the command line, using popen. If you are familiar with fopen, it works exactly the same. So, for example, you could write
```

...
  FILE *FP;
  char line[100];

  FP = popen ("./program < input_file", "r");
  fgets (line, sizeof line, FP);
...

```
To run FP and then read one line of its output. Just like a file, you can continue running fgets() or whatever other function you may need to keep reading output until you get to the EOF at the end.

For your purposes, this is probably the best way. If you needed to both read data from the program and write to it (simulating keyboard input once the program was already running), you would have to write a more complicated program using fork() and exec(), but for the program you are describing popen() should be enough.

Good luck with your project!

P.S. You may find that Googling for terms like "c link fortran" wasn't very helpful. This is because there is a very, very complicated process also called linking used to connect C and Fortran libraries together, but it is definitely not what you are looking for. It involves making .so files like the ones that fill /usr/lib and doing messy things from there.

---

### Post by ubun_tut on 2009-11-09
hi thanks for the info. i have actually found what i was looking for: the 'system' command. this allows me to call shell scripts from c, and its as straightforward as i dare to imagine.

---

