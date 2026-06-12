---
title: "install man c"
date: 2006-04-04
forum: General Help
---

### Post by tanaka on 2006-04-04
I'm programming in C language and I need to use the man pages but I can't acces them. I've tried to install the documantation with Synaptic but man does not support c programmig.

I've tried also with

       sudo apt-get install glibc-doc

but nothing.  :-k 

:confused: How can I solve my problem? 
Is there someone can give me some hints?

---

### Post by dcstar on 2006-04-04
[QUOTE=tanaka]I'm programming in C language and I need to use the man pages but I can't acces them. I've tried to install the documantation with Synaptic but man does not support c programmig.

I've tried also with

       sudo apt-get install glibc-doc

but nothing.  :-k 

:confused: How can I solve my problem? 
Is there someone can give me some hints?[/QUOTE]
**man gcc** works fine for me.

---

### Post by catlett on 2006-04-04
Are you typing the command in the terminal. In the terminal you type man and then the name of the program you want. I don'y know the name of the C program but for the sake of argument. If you wanted to know about apt type ```
man apt
```
Didn't see the pther post type man gcc in the terminal.

---

### Post by localzuk on 2006-04-04
What documentation are you wanting? Are you wanting information on how to use c? Or are you wanting info on how to use gcc?

If gcc, follow the other posts regarding man gcc. There isn't a man page for the c language and if there was it would not likely be the best place for information on how to program c - a good book would help with this.

---

### Post by hw-tph on 2006-04-05
The manpages-dev package has programming related man pages (glibc documentation and so on) - most likely what you're looking for. So **sudo apt-get install manpages-dev** should help you out.


Håkan

---

