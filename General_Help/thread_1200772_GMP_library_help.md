---
title: "GMP library help"
date: 2009-06-30
forum: General Help
---

### Post by milikox on 2009-06-30
Hello everyone, I m new here

I really need some help using GMP

i searched the boards before actually posting this thread but couldnt find my way out :P

well 

First of all, i downloaded the package, unzipped it, configured it etc

but when i try to include the gmp library gcc says that "there was an error, cant find gmp.h" or something like that

i really cant understand why this happens, i followed the steps that are descriped in gmp's team page.

After helping me with that issue, i would  be really grateful if you could show me some simple program using gmp library, for example:

Show me how the code should be if we want to calculate the sum of two 10 digit numbers.

Thank you very much.

---

### Post by ChaiTan on 2009-06-30
Install GMP development files using:
```
sudo apt-get install libgmp3-dev
```
Follow tutorials on the net on how to write a program using gmp.
then compile the program using
```
gcc file.c -o file -lgmp
```

---

### Post by michy99 on 2009-06-30
Did you install using the method described here?```
http://gmplib.org/manual/Installing-GMP.html#Installing-GMP
```

You can install gmp from the repositories.```
sudo apt get install libgmp3c2 libgmp3-dev libgmp3-doc
```

---

### Post by milikox on 2009-06-30
thanks for the replies,

michy99 yes i installed it from that link

---

