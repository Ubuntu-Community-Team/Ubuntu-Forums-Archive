---
title: "Help Converting .bat file"
date: 2011-04-23
forum: General Help
---

### Post by rm4453 on 2011-04-23
Hello I have been searching for weeks trying to convert a batch file so that I could use it I would really appreciate if someone would convert it for me... :guitar:I will put the download link on my next post I mainly want to know that someone is willing to convert if before i give the scripting away....

---

### Post by AlphaLexman on 2011-04-23
A batch file is regarded as a ms-dos file in these forums, you may not get a candidate without seeing the code. If the code is personal, most people here are open-source advocates.

With that in mind, what format do you want to convert it to? bash, perl, python, zsh, posix?

You might get more help by identifying more info about your goals.

Good luck!

---

### Post by fdrake on 2011-04-23
if i understand u are converting a text file from windows to unix right? ....   well you can use fromdos command

ex.
fromdos windows_file.bat 

on the other end if you want to convert from unix to windows use: todos
ex
todos unix_file.bat 

i hope this is what your are talking about....

---

### Post by rm4453 on 2011-04-23
> **AlphaLexman said:**
> A batch file is regarded as a ms-dos file in these forums, you may not get a candidate without seeing the code. If the code is personal, most people here are open-source advocates.

With that in mind, what format do you want to convert it to? bash, perl, python, zsh, posix?

You might get more help by identifying more info about your goals.

Good luck!
I am sorta new to anything except for .bat creation, I would just like to get it converted so that I can use it on my Kubuntu 10.04 power PC... If you will convert it for me I will email you the source code, but you must promise not to give anything in it away.... If you will convert it email me at rm4453(at)gmail.com with the subject KeyGenPls... :guitar:

---

### Post by WorMzy on 2011-04-23
> **fdrake said:**
> if i understand u are converting a text file from windows to unix right? ....   well you can use fromdos command

ex.
fromdos windows_file.bat 

on the other end if you want to convert from unix to windows use: todos
ex
todos unix_file.bat 

i hope this is what your are talking about....

tofrodos just converts the linebreaks, it doesn't turn a bat file into a shell script.


There is no easy way of converting a bat file, and there's no guarantee that the desired behaviour is reproducible on Linux.

---

