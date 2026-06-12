---
title: "command not found when using terminal"
date: 2010-08-25
forum: General Help
---

### Post by workshop1702 on 2010-08-25
hi just bought two new monitors , having major problems installing them,ubuntu 10.04 didnt recognize them at all running at 800x600 they should run at 1920x1080.
i have found various web pages explaining how to adjust the resolution using terminal . the problem i am having that nearly every command i put in commes back with command not found , i thought i needed to be signed in asroot so did this but still the same problem .
I just cannot work out what i am doing wrong, could someone help please.

---

### Post by Vaphell on 2010-08-25
you haven't mentioned what commands you tried and what gfx is present in your pc.

---

### Post by llamabr on 2010-08-25
Do this:

1. open a terminal
2. type in some command that's not working
3. look at the error, and grumble to yourself
4. copy/paste the whole thing back here.

without knowing what your problem is, no one can help you.

---

### Post by WorMzy on 2010-08-25
Also, post the output of
```
echo $PATH
```

---

### Post by workshop1702 on 2010-08-26
this is what i get when putting in what you suggest  echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
root@andrew-desktop-workshop:~# 

my graphics card is a dual head matrox g450 card

---

### Post by Lars Noodén on 2010-08-26
Those cover the locations you are likely to find a program.  What program are you trying to run?  Is the program installed?  

The people writing the tutorial might have other systems with other defaults and maybe additional tools added just for the task at hand.

---

