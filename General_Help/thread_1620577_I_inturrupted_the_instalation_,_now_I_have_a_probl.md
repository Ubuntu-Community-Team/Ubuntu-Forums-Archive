---
title: "I inturrupted the instalation , now I have a problem"
date: 2010-11-13
forum: General Help
---

### Post by zer2 on 2010-11-13
i was installing Kopete and I inturrupted the instalation , now I have a problem. 

When I want to install something I get:  > E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I don't have the slightest idea how to fix it. is there any way to go back in time like in windows when it was working or maybe there's quick solution ?

**edited:** I have ubuntu 10.04

---

### Post by lmarmisa on 2010-11-13
Try to follow the instructions.

Open a terminal (Applications -> Accesories -> Terminal) and type this command:

> 
sudo dpkg --configure -a


---

### Post by zer2 on 2010-11-13
> **lmarmisa said:**
> Try to follow the instructions.
Open a terminal (Applications -> Accesories -> Terminal) and type this command:OK and now what should i do ?

> dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libqtcore4 (= 4:4.6.2-0ubuntu5.1); however:
  Version of libqtcore4 on system is 4:4.6.2-0ubuntu5.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqtgui4


---

### Post by lmarmisa on 2010-11-13
Try this command:

> 
sudo apt-get -f install


---

### Post by zer2 on 2010-11-13
> **lmarmisa said:**
> Try this command: Thank you so much... It worked like a charm :D

---

### Post by lmarmisa on 2010-11-13
Great!!!. :P

Please, mark the thread as SOLVED.

---

