---
title: "Cannot link libraries to g++"
date: 2011-05-18
forum: General Help
---

### Post by sangsterthegangster on 2011-05-18
Ok ive been trying to use the library boost/thread.hpp but i cant get it to link. Every time i try it looks like this:
```
tyler@TjLaptop01:~/Desktop$ g++ thing.CPP -o Desktop -lboost_thread
/usr/bin/ld: cannot find -lboost_thread
collect2: ld returned 1 exit status

```
This might be a noob question lol but what do i do to get it working? I cant find much on it. Thank you in advance.

---

### Post by __Sun__ on 2011-05-18
You need to specify the location of the library with the I or L flag. Both work, really.

E.g., if library libfoo.[a|so] is in a directory called /home/usr/lib/ then you'd do this:
```
g++ -L/home/usr/lib -lfoo **...**
```It depends where you installed the library. If you installed it through apt-get then there shouldn't be any problem.

EDIT:
Are you sure the library name is boost_thread?
The name could be incorrect, check the boost library manual and decipher the right name.
I don't use boost so I can't help there.

---

### Post by sangsterthegangster on 2011-05-18
Well i did install it through apt-get. Its weird, i also installed ncurses through apt-get and it works but nothing i try will get boost to link.
Its in my "/usr/include" folder as boost so i tried *-lboost* , but still no luck. What am i doing wrong?

---

