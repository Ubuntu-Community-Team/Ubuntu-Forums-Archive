---
title: "Ubuntu software problem"
date: 2011-01-27
forum: General Help
---

### Post by peskovic on 2011-01-27
I have a big problem with Ubuntu software products center. I installed pjthom 2.6, 2 days ago when something I try to install ubuntu software products over the city throws me the following (it's a maverick 10:10)

   [http://www.dodaj.rs/f/1M/XH/4ndoFoE6/snimak-ekrana-1.png](http://www.dodaj.rs/f/1M/XH/4ndoFoE6/snimak-ekrana-1.png) 

 I hope there is a solution, because there would be just to re-install ubuntu 10:10, by I do not know which way

I hope to have a solution?:(

---

### Post by peskovic on 2011-01-27
bump...please help :(

---

### Post by Krytarik on 2011-01-27
Enter the following commands in a terminal:
```
sudo dpkg --configure -a
```
when given a dialog box, where you have to select <Ok>, press "Tab" to get to it, then press enter
```
sudo apt-get install -f
```
Post back, what happened.
If you get errors and this doesn't solve the issue, then post the error messages as well, in code-tags (#) please.

---

