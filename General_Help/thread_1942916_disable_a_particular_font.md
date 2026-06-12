---
title: "disable a particular font"
date: 2012-03-18
forum: General Help
---

### Post by winzip on 2012-03-18
I  have installed ubuntu 10.  When I type  locale -a  in terminal, I find many fonts installed.

I want to disable a particular font  temporarily...what is command/steps to do that ?


How do I enable later ?

---

### Post by jerrrys on 2012-03-18
[https://wiki.ubuntu.com/Fonts#Manually](https://wiki.ubuntu.com/Fonts#Manually)

and if you have a desktop (GUI) just open a terminal and enter:

gksudo nautilus

and navigate to the files

and welcome to the forum

---

### Post by winzip on 2012-03-18
> **jerrrys said:**
> [https://wiki.ubuntu.com/Fonts#Manually](https://wiki.ubuntu.com/Fonts#Manually)
and navigate to the files

thanks for the reply.

comments not  understood.

which file need the modification ?  I see wiki link telling fonts location.

/etc/fonts/fonts.conf;

OR

/usr/share/fonts, 

OR

/usr/local/share/fonts, 

OR

and /home/<username>/.fonts


So, I'm confused which file need the modification .. how do you decide that ?


How do you disable a particular font and enable later ?

---

### Post by jerrrys on 2012-03-18
Perhaps if I better understood your need to disable/enable fonts I could give a better answer.

Maybe something like "font-manager"

To install open a terminal and enter:

sudo apt-get install font-manager

then in terminal enter:

gksudo font-manager

---

### Post by winzip on 2012-03-18
> **jerrrys said:**
> Perhaps if I better understood your need to disable/enable fonts I could give a better answer.

Maybe something like "font-manager"

To install open a terminal and enter:

sudo apt-get install font-manager

then in terminal enter:

gksudo font-manager

I'm afraid these commands may not work in a Ubuntu 10  server without GUI...am I correct ?

how do I  work it out ?

---

### Post by jerrrys on 2012-03-18
you are correct

---

### Post by winzip on 2012-03-18
> **jerrrys said:**
> you are correct

whats the alternative solution ?

---

