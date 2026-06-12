---
title: "Using the Terminal to Launch Programs"
date: 2009-06-27
forum: General Help
---

### Post by damnhappy on 2009-06-27
I would like to be able to use the terminal to launch a program. I have found a solution, but it seems like an inelegant one. I have the program in my home folder and in my /home/myname/bin folder. If I have the program in both locations I can launch it from the terminal. If I remove it from one of the locations say /home/myname/bin, and  leave a copy only in /home/myname, it won't launch from the terminal. I have reversed it too, and it still won't work. It just seems strange that i have to have the program in both locations for it to launch from terminal. 
Is there a way to fix this?

---

### Post by philcamlin on 2009-06-27
if its installed 

sudo "program goes here" :popcorn:

---

### Post by kerry_s on 2009-06-27
> **damnhappy said:**
> I would like to be able to use the terminal to launch a program. I have found a solution, but it seems like an inelegant one. I have the program in my home folder and in my /home/myname/bin folder. If I have the program in both locations I can launch it from the terminal. If I remove it from one of the locations say /home/myname/bin, and  leave a copy only in /home/myname, it won't launch from the terminal. I have reversed it too, and it still won't work. It just seems strange that i have to have the program in both locations for it to launch from terminal. 
Is there a way to fix this?

it only needs to be in ~/bin so you must be doing something wrong.
check that it is executable, try logging out and back in at least once.

---

### Post by credobyte on 2009-06-27
Use *alias* : [http://www.mediacollege.com/linux/command/alias.html](http://www.mediacollege.com/linux/command/alias.html)
```
alias runmyapp='/etc/myapp_path/launcher'
runmyapp
```

---

### Post by ~sHyLoCk~ on 2009-06-27
You can also use tab for auto-completion. E.g. -> fir<tab> for firefox

---

### Post by gldearman on 2009-06-27
Make sure /home/myname/bin/ is in your path.

What is the output of the following?

```
$PATH
```

---

### Post by kerry_s on 2009-06-27
> **gldearman said:**
> Make sure /home/myname/bin/ is in your path.

What is the output of the following?

```
$PATH
```

it's always in path when created, loaded by ~/.profile, you can check to see.

---

