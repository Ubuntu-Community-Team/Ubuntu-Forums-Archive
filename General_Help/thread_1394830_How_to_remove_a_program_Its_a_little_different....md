---
title: "How to remove a program??? Its a little different..."
date: 2010-01-31
forum: General Help
---

### Post by vampirelazarus on 2010-01-31
Ok... I, being not bright when tired, try to install avast4server on my laptop. One problem, my laptop is 32-bit and avast4server is only 86-bit.  

Now when I try to install programs through the Ubuntu Software Center,  I get this:

   The installation or removal of a software package failed.

clicking on details gives me this:

   E:I wasn't able to locate file for the avast4server package. This might mean you need to manually fix this package.: 


Trying something else, my computer now starts with a little error:
  E: The package avast4server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


When I go to reinstall it (using apt-get in the terminal) i get the same thing.

using dpkg -r to remove it i get:
  dpkg: error processing avast4server (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 avast4server


How in the world do I resolve this? I just want to get rid of it so i can install programs...

---

### Post by lisati on 2010-01-31
Um 86-bit? :confused: Sounds interesting. But that's beside the point.... :D

Did you try what the error message sugested, i.e. reinstalling and then removing it? (edit: oh you did try reinstalling it)
Did you try the following? ```
dpkg --configure -a
``` (edit: that's from the command line....)

---

### Post by vampirelazarus on 2010-01-31
> **lisati said:**
> Um 86-bit? :confused: Sounds interesting. But that's beside the point.... :D

Did you try what the error message sugested, i.e. reinstalling and then removing it? (edit: oh you did try reinstalling it)
Did you try the following? ```
dpkg --configure -a
``` (edit: that's from the command line....)


Yes.. I just tried it with the same results...

Whats meant by 86-bit is x86... if thats not an 86-bit, then I dont know what Im talking about...

---

### Post by spiky001 on 2010-01-31
I think you will find it's 1386 x86  then theres 64 bit dont know how 86 is relivent but it is for 32bit system. 64 is for 64bit system i,m sure i,m right plz correct me if i,m wrong

---

### Post by vampirelazarus on 2010-01-31
If thats the case, then shouldnt it install?

---

### Post by SemiBuz on 2010-01-31
x86 - 32bit 
x86_64 - 32/64bit ( universal )
x64 - 64bit

Anyway, you can use find and -exec to remove it from your system.

---

### Post by theozzlives on 2010-01-31
> **SemiBuz said:**
> x86 - 32bit 
x86_64 - 32/64bit ( universal )
x64 - 64bit

Anyway, you can use find and -exec to remove it from your system.

i386 = 32 bit
AMD64 = 64 bit

If you're running 64 bit, and you got it from the repositories it  should fit your architecture. Try```
sudo apt-get install -f
```

---

### Post by vampirelazarus on 2010-01-31
> **SemiBuz said:**
> x86 - 32bit 
x86_64 - 32/64bit ( universal )
x64 - 64bit

Anyway, you can use find and -exec to remove it from your system.

how would that be typed into the terminal?

EDIT: Nevermind... I just had to scroll down the man page some more...

---

### Post by SemiBuz on 2010-01-31
```
find / -name avast* -exec rm -r {} \;

``````
locate avast
```If it returns 0 results, you've removed it.

[COLOR=Red]** Use with care - invalid search pattern can be a fatal mistake.

[/COLOR]> **theozzlives said:**
> i386 = 32 bit
AMD64 = 64 bit

If you're running 64 bit, and you got it from the repositories it should fit your architecture. Try```
sudo apt-get install -f
```

i686 - x86_64 :)

---

### Post by vampirelazarus on 2010-01-31
Its saying it cant find an archive for it?

---

### Post by vampirelazarus on 2010-01-31
I still have the problem... its not solved.

---

