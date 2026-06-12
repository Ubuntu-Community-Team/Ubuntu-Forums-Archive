---
title: "Linux console question"
date: 2010-12-25
forum: General Help
---

### Post by yanes on 2010-12-25
Salam for every body :)

please I'm relatively new to linux ,

when some programs fails ( they shows a blank window with no controls , any action or click responds except the window MAX and MINIMIZE ) 

what have i to do ?

in the system monitor (under gnome ) process lists i don't find the process name , so can i get a list of processes in the terminal ? 

I tried the " ps " command but it returns processes running under the current console only :( 

how to list all system processes in the terminal (including windowed programs)

thank you in advance

---

### Post by bouncingwilf on 2010-12-25
ps -ef will give a full listing of all processes running

ma'a salaam

bouncingwilf

---

### Post by yanes on 2010-12-25
Yes , it works thank you !

---

### Post by TeoBigusGeekus on 2010-12-25
Try
```
pstree
```
for fun.

---

### Post by mysteriousdarren on 2010-12-25
You could always just kill the window.

---

### Post by yanes on 2011-03-09
> **mysteriousdarren said:**
> You could always just kill the window.

when the close button is natively disabled by the program , there's no way to kill it as know 

but terminal solutios are usually more capable to manage and kill processes

---

