---
title: "executing c++  file"
date: 2010-04-06
forum: General Help
---

### Post by kakarala on 2010-04-06
Hi 
I am executing a .cc file using the following command 

gcc -03 lib.o seq_gen.cc -o seq_gen

but its giving me error 

gcc: unrecognized option '-03'
/usr/bin/ld: lib.o: Relocations in generic ELF (EM: 2)
/usr/bin/ld: lib.o: Relocations in generic ELF (EM: 2)
lib.o: could not read symbols: File in wrong format
collect2: ld returned 1 exit status

does anyone know about this?

---

### Post by falconindy on 2010-04-06
gcc is the C compiler. You want g++ instead. Also, the option is -O2 (the letter O and the number 2), not -02 (the number 2 padded with a zero).

---

### Post by kakarala on 2010-04-06
I used the command 

 g++ -o2 lib.o seq_gen.cc -o seq_gen

it gives error 

/usr/bin/ld: lib.o: Relocations in generic ELF (EM: 2)
/usr/bin/ld: lib.o: Relocations in generic ELF (EM: 2)
lib.o: could not read symbols: File in wrong format
collect2: ld returned 1 exit status

---

### Post by falconindy on 2010-04-06
The file you're compiling against is malformed according to the compiler. Where did you get this file from?

Also, it's a capitol O, not a lowercase o.

---

### Post by kakarala on 2010-04-06
I downloaded this file from the website 
do you think the file is corrupted

---

### Post by falconindy on 2010-04-06
No idea what "the website" is. I'm not going to say its corrupt, but I think ld knows better than you or I when it says the file is in the wrong format.

---

### Post by lisati on 2010-04-06
> **kakarala said:**
> I downloaded this file from the website 
do you think the file is corrupted

Which website?

---

### Post by kakarala on 2010-04-06
i downloaded the file from this website 

[http://www.eecs.umich.edu/acal/software/seq_gen/download.html](http://www.eecs.umich.edu/acal/software/seq_gen/download.html)

lib.o file is in that rar file

---

### Post by falconindy on 2010-04-06
```
$ file lib.o
lib.o: ELF 32-bit MSB relocatable, SPARC, version 1 (SYSV), not stripped
```
Wrong architecture. Without the source, you won't be able to compile this.

---

### Post by kakarala on 2010-04-07
what do you mean by source?

---

### Post by lisati on 2010-04-07
> **kakarala said:**
> what do you mean by source?

[http://en.wikipedia.org/wiki/Source_code](http://en.wikipedia.org/wiki/Source_code)

---

