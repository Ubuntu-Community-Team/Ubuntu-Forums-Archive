---
title: "nightmare of a time with LPR"
date: 2012-04-10
forum: General Help
---

### Post by dazman19 on 2012-04-10
I have oneric on my machine and i can do lpr


but on the new print server i set up to print my scripts it wont print with LPR

daryl@printing:~$ lpstat -ti
scheduler is running
no system default destination
device for lablabel: socket://192.168.58.190:9100
lablabel accepting requests since Wed 11 Apr 2012 15:35:53 NZST
printer lablabel is idle.  enabled since Wed 11 Apr 2012 15:35:53 NZST
	Ready to print.
daryl@printing:~$ lpr -P lablabel testtext.txt 
lpr: lablabel: unknown printer
daryl@printing:~$ 

I do not understand what the problem is and I am pretty exhausted with troubleshooting.

I have definately got this working on my other oneric installation, but this fresh install doesnt seem to work..

---

### Post by dazman19 on 2012-04-11
Ok it seems cups has its own version of lpr.

SO removing lpr was the first step.

It seems like cups has been ported to debian/ubuntu from BSD. So i installed cups-bsd

It started working fine. So i got the beast going on ubuntu.

Just need to get it working on the debian servers now.

---

### Post by dazman19 on 2012-04-11
I am still having problems. It says the print jobs are completed, But nothing is coming out of the printer. 

I googled it and it seems loads of people have had the same issue but i am still struggling to find a fix.

---

