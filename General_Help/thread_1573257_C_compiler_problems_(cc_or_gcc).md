---
title: "C compiler problems (cc or gcc)"
date: 2010-09-12
forum: General Help
---

### Post by thook07 on 2010-09-12
hey guys,

I'm having a problem reading an input text file in a c program.
What I would like to know is the syntax of compiling the program.
i have a test.c file that needs the input1.txt file as an input. 
how would I write this in the terminal??

cc -c test.c > input1.txt   ?????

I've been looking around but can't seem to find anything

Any help would be appreciated

---

### Post by gmargo on 2010-09-12
To compile a c program (used "test1.c" to not conflict with the "test" program):
```

gcc -o test1 test1.c

```To run that program with input1.txt as an argument:
```

./test1 input1.txt

```To run that program with input1.txt fed in as standard-input:
```

./test1 < input1.txt

```

---

### Post by thook07 on 2010-09-12
Thank you very much!

Exactly what I was looking for

---

