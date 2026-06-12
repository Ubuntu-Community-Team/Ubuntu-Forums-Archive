---
title: "E: Couldn't find package"
date: 2010-06-18
forum: General Help
---

### Post by arunkrishnan on 2010-06-18
E: Couldn't find package
this is the message I'm getting whenever I try to install any package in terminal using $sudo apt get install

---

### Post by ankit singh on 2010-06-18
its sudo apt-get install package, there is '-' in between apt and get. Sometimes u need to give explicit package name to what u want to install.For ex. u cannot install php like this sudo apt-get install php it will show same error.The correct for this is sudo apt-get install php5.So it is recommended to use synaptic.

---

### Post by arunkrishnan on 2010-06-18
I had entered the instructions in correct format itself, thats not the problem
Following are few comments that shows the same error

sudo apt-get install vim-full
sudo apt-get install avant-window-navigator awn manager

---

### Post by howefield on 2010-06-18
> **arunkrishnan said:**
> I had entered the instructions in correct format itself, thats not the problem

Yes it is the problem, you are entering the wrong instructions.

> sudo apt-get install vim-full
sudo apt-get install avant-window-navigator awn manager

The first one vim-full isn't in the repository, and awn manager doesn't exist, remove it from the line and try

sudo apt-get install avant-window-navigator

---

### Post by arunkrishnan on 2010-06-18
ya u are right
it was my mistake, Sorry
The problem solved
Thanks.........

---

