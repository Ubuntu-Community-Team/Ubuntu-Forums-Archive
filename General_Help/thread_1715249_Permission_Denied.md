---
title: "Permission Denied"
date: 2011-03-26
forum: General Help
---

### Post by trooper88 on 2011-03-26
Hello,

I'm fairly new to linux but ive used it for some C programming before. Currently i am doing 16 bit assembly, so i had to install ubuntu 32 bit to get around my 64 bit Windows 7.

Well ive ran into some problems and im hoping you guys can help. Ive got this file from my text book and in order to use it you have to navigate to the examples file in the terminal and type ./t88 "examplefilename". 

Well my problem is i get this back:

trooper88@ubuntu:~/Desktop/linux/examples$ ./t88 hllowrld
bash: ./t88: Permission denied

can anyone help? my teacher is very harsh on the fact that we have to use only this assembler

the ./t88 is supposed to pull up a program tracer, and the ./s88 is supposed to run the program


any help would be greatly appreciated :)

[URL="http://www.mediafire.com/?hnbiv54gp5byqse"]
http://www.mediafire.com/?hnbiv54gp5byqse[/URL]

The examples file  is in the /8088_tra/linux/examples

---

### Post by idoitprone on 2011-03-26
do you have executable permissions

```
ls -l t88
-rw[SIZE=3]**x**[/SIZE]r--r--
```

```
chmod u+x t88
```

---

### Post by blind2314 on 2011-03-26
You'll also need to add execute permissions to the "s88" file that actually runs your programs, pretty much anything that needs to be "ran" should be executable.

---

### Post by trooper88 on 2011-03-26
Thank you both, it works like a charm now :D

Now on to learning!

---

