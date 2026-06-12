---
title: "CAN'T save Environment Variables"
date: 2010-02-12
forum: General Help
---

### Post by siukimfong on 2010-02-12
in terminal, I use the command " export XXX="xxx" " to creat a new environment variable, and then " env | grep XXX " to check if it is existed. but when I run the terminal again, the variable I created is disappeared. I've found it just can't save the varibles I created.. 

what's the solution?  :confused:

---

### Post by jken146 on 2010-02-12
[http://www.mcsr.olemiss.edu/unixhelp/environment/env3d.html](http://www.mcsr.olemiss.edu/unixhelp/environment/env3d.html)

---

### Post by ramsrom on 2010-02-12
It will be gone after you close the terminal. To save it, just write

export XXX="xxx"
 
to your .bashrc file. Then it will be set when you login to your machine
(if your default shell is bash of course)

You find the .bashrc file under /home/yourLoginName/.bashrc

---

### Post by siukimfong on 2010-02-12
> **ramsrom said:**
> It will be gone after you close the terminal. To save it, just write

export XXX="xxx"
 
to your .bashrc file. Then it will be set when you login to your machine
(if your default shell is bash of course)

You find the .bashrc file under /home/yourLoginName/.bashrc

thank you so much! I make it with your solution! :D

---

