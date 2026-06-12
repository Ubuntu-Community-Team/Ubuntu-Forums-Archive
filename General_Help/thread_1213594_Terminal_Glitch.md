---
title: "Terminal Glitch"
date: 2009-07-15
forum: General Help
---

### Post by dumblebee100 on 2009-07-15
I have a problem with terminal lately 

I have many keyboard shortcuts and terminal is one of them ..
I have kept CTRL+ATL+T as my terminal shortcut and terminal command is
```
gnome-terminal --geometry=+400+400
```

The problem is I get default path to /    instead of my $home folder 
everytime I have to change directory to my $home dir to access things ...well its not difficult but it seems uncomfort ( **upper terminal in screenshot**) 

well If I access the terminal from APPLICATIONS--> ACCESSORIES-->TERMINAL 

then I get $home path by default (**lower terminal in screenshot**)

further information why I may be getting like this ...I happened to give every authorization to my user account .....is that the problem to get root dir everytime I open a terminal through keyboard shortcut

---

### Post by dumblebee100 on 2009-07-26
Im expecting some replies folks ....

---

### Post by dumblebee100 on 2009-08-18
Why dont I get some reply for this ...

did I ask a impossible question or what ...or else you people dont use terminals in linux

---

### Post by Dakiraun on 2009-08-18
Lack of replies is often just folks being unsure about what's going on, which I admit is what I'm wondering.  

I'm not sure why it's preferring the root directory when you start it, but if you edit your shortcut and add the parameter "--working-directory=~", it should start in your home directory.  Not a fix so much as a way around the problem.

---

### Post by dumblebee100 on 2009-08-18
> **Dakiraun said:**
> Lack of replies is often just folks being unsure about what's going on, which I admit is what I'm wondering.  

I'm not sure why it's preferring the root directory when you start it, but if you edit your shortcut and add the parameter "--working-directory=~", it should start in your home directory.  Not a fix so much as a way around the problem.

You made my day buddy

now I need not change everytime when I start terminal 

this happens when we don't read the man pages completely ...

---

### Post by Dakiraun on 2009-08-19
> **dumblebee100 said:**
> You made my day buddy

now I need not change everytime when I start terminal 

this happens when we don't read the man pages completely ...

No one reads man pages completely. :P  Glad it helped.

---

