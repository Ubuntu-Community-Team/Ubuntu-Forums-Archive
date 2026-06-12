---
title: "How do I set myself up as Root/Administrator"
date: 2009-12-22
forum: General Help
---

### Post by speedygonzalas on 2009-12-22
Hi, I need to make a revision to the file /etc/modules through text editor but do not know how to give myself the appropriate access in order to make a change. 
I tried using sudo -i and sudo su from the terminal and it didn't work. Can someone please help me?

---

### Post by bodhi.zazen on 2009-12-22
The first user has admin privileges via sudo and gksu.

What is nto working exactly ?

sudo -i

Enter your log in password , you will not see anything as you type, hit enter.

---

### Post by speedygonzalas on 2009-12-22
i did that and it works just as you said with the result showing root in front of my name in the terminal, except when I opened /etc/modules through text editor, and added the code: 
ndiswrapper
at the end of it, it didn't let me save it, it would show the message 
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."
and leave me. This is driving me nuts cuz I have no clue what to do now.

---

### Post by speedygonzalas on 2009-12-22
Nvm I just used
 
gksudo nautilus

and made the changes, worked great.
Thanks alot for the help anyways.

---

### Post by DukeBoxer on 2009-12-22
Can't you just type in sudo gedit /etc/modules and edit the file.  I would think that would work and you would open it up as "root"

---

### Post by bodhi.zazen on 2009-12-22
> **DukeBoxer said:**
> Can't you just type in sudo gedit /etc/modules and edit the file.  I would think that would work and you would open it up as "root"

That will work, but gksu is preferred for graphical applications such as nautilus or in your example gedit.

---

### Post by DukeBoxer on 2009-12-22
Thanks for explaining that! I didn't really understand the differences.

---

