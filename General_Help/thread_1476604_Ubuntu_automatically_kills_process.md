---
title: "Ubuntu automatically kills process?"
date: 2010-05-08
forum: General Help
---

### Post by Tiger257 on 2010-05-08
Hi everyone,

I wrote a program in C that will generate a matrix for me and write it to a file.  I'm trying to use it to generate a 100,000 x 100,000 matrix of ints, but after about 30 minutes the shell kills the process and the program terminates.  I've gotten it to generate a 50,000 x 50,000 matrix, but I don't understand why 100,000 doesn't work?  

I thought about memory constraints, but I have 8 gb ram and a 20 gb swap partition.  Also, the program successfully malloc's the space for 100,000x100,000 ints, but after initializing 40% of the entries the program gets killed.

Is this just because Ubuntu thinks the process is taking too long and kills it automatically, or for some other reason?  Are there any ways to manipulate the settings so that a process is never killed automatically?

Thanks!

---

