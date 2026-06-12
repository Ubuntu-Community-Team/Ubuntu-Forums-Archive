---
title: "Evolution re installation problem-- pls help"
date: 2011-04-19
forum: General Help
---

### Post by medneo on 2011-04-19
Hi all,

I recently switched to ubuntu from win 7. I have samsung netbook150.
I did stupid mistake in setting up evolution. So I uninstalled it first via ubuntu software center and again reinstalled it. 
I also installed all the evolution components from synaptic package manager. 
Now I dont see evolution in internet section of Applications on the top panel. 
I need your help to figure out how I can reinstall evolution properly and access it again.
I would really appreciate your help.

Tushar

---

### Post by wojox on 2011-04-19
Look in the Office section. Sometimes it's in there.

---

### Post by nitstorm on 2011-04-19
Take a look at Wojox's advice. You can also try hitting **Alt+F2** and typing evolution and running it from there.

For a re-install:
This removes evolution (everything of evolution including config files:
```
sudo aptitude purge evolution
```  

This installs evolution:
```
sudo aptitude install evolution
```

---

### Post by dcstar on 2011-04-20
> **medneo said:**
> Hi all,

I recently switched to ubuntu from win 7. I have samsung netbook150.
I did stupid mistake in setting up evolution. So I uninstalled it first via ubuntu software center and again reinstalled it. 
I also installed all the evolution components from synaptic package manager. 
**Now I dont see evolution in internet section of Applications on the top panel.** 
..........

It has** not** been listed there for over a year now. Launch Evolution by selecting the mail (envelope) icon at the top RHS of the screen.

---

### Post by medneo on 2011-04-22
Hi guys,

Thank you so much for your replies. 
I listened wojox's advice about looking office in application section. Evolution was there, I felt so dumb. 
Thank you sending unistalling and reinstalling codes for evulution.
I am enjoying my new ubuntu 10.04, no regrets to change from win 7. 
I am showing off my netbook ubuntu to all my friends and I can feel, they are all jealous. :P

---

