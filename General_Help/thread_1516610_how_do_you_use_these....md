---
title: "how do you use these...?"
date: 2010-06-24
forum: General Help
---

### Post by killer62491 on 2010-06-24
hey all, i recently dl'ed a package in the .tar.bz2 format, which i didn't realize it was in said format... lol. now i know that these .tar.*** (where as ***=whatever it may be) are very commonly used in linux systems, but how would one use the specific package type aforementioned...? is it poaaible to run it as a program/application? if so, how would one do so? the reason why i'm asking is because its a game, as in the package as a whole ***is*** the game. i don't see any way to mount a file of this type, but i remember that it is possible to make it an executable. would that be the way to go? please let me know. 
many thanks ubucrew! also, it didnt autoinstall the package once done dl'ing...

.::ALPHA::HECTOR::SIERRA::.


P.S. i like that term, i just thought of it^.^ (ubucrew)

---

### Post by Smart Viking on 2010-06-24
What game is it? :)

---

### Post by killer62491 on 2010-06-24
it's runescape lol... i just felt like messing with their source code so yeah.....

---

### Post by killer62491 on 2010-06-24
and i gots a question lol, do you have a clue in the darned blue nameless hell on earth how one would manage to run it? =P

---

### Post by BenAshton24 on 2010-06-24
Extract it with archive manager
Compile the code (Instructions in readme (probably))
Run It

---

### Post by killer62491 on 2010-06-24
and how would one "compile code"?
 lol im kinda new to coding..... so a simple explanation is best.

.::ALPHA::HECTOR::SIERRA::.

---

### Post by lisati on 2010-06-24
> **killer62491 said:**
> and how would one "compile code"?
 lol im kinda new to coding..... so a simple explanation is best.

.::ALPHA::HECTOR::SIERRA::.

Instructions are (probably) in the README file. One common approach is:
```
./configure
make
make install

```

---

### Post by BenAshton24 on 2010-06-24
> **ghdfans2010 said:**
> What game is it? I want to have a try.
Perhaps reading is a skill that you would like to try first?
> **killer62491 said:**
> it's runescape lol... i just felt like messing with their source code so yeah.....

Here is a more thorough explanation.

1. Navigate to the directory (folder) in which your downloaded tar.bz2 is located.
2. Double click on the file
3. Click extract on the top toolbar.
4. Chose a directory in which to extract it.
5. Click Application -> Accessories -> Terminal
6. Change to the directory in which your extracted archive resides by using the following commands "ls" (lists the contents of the current directory), "cd" (changes to a different directory). Here is an example of how to do this:
```
[ben@ben-desktop ~]$ ls
Software            Christianity
Desktop             Documents
Downloads           Music
Pictures            Videos
Programming
[ben@ben-desktop ~]$ cd Downloads
[ben@ben-desktop Downloads]$ ls
Archive
[ben@ben-desktop Downloads]$ cd Archive
```
7. Now type "gedit README" (without quotes)
8. Press Enter
9. The instructions on how to compile the source should be here. If they are not then close gedit.

=== Follow instructions if they exist, proceed if they don't ==

10. type "./configure" (without quotes)
11. If there are no errors proceed to step 12, if there are errors then post them here.
12. type "make && make install" (without quotes)
11. If there are no errors then you have successfully compiled and installed it, if there are errors then post them here.

Hope this helps,
Ben.

---

### Post by killer62491 on 2010-08-08
yeah sorry for taking so long to get a response in, but work had me tied up. ok so the "./configure" command gave output: 
austin@ubuntu:~/Desktop/jagexlauncher-src$ ./configure
bash: ./configure: No such file or directory
but then i decided to see if it would still do the other part of the compiling, which was: 
austin@ubuntu:~/Desktop/jagexlauncher-src$ make && make install
make: *** No targets specified and no makefile found.  Stop.
so what does it all mean...?

---

