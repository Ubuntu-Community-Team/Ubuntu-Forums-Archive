---
title: "can't get gnuplot to work"
date: 2011-04-11
forum: General Help
---

### Post by technmom on 2011-04-11
I have installed gnuplot but nothing appears when I tell it to plot sin(x)

I'm using Ubuntu 10.4 and downloaded gnplot 4.4.3 
I need it for a class assignment

If you think I should go to another area of the forum.....just direct me there.

thanks,
tm

---

### Post by wt8008 on 2011-04-13
Please explain in more detail what exactly you did or tried to do to start gnuplot and to plot the sin(x) function.

---

### Post by rosencrantz on 2011-04-13
Did you set a non-X terminal (like ps or png)?

---

### Post by rosencrantz on 2011-04-13
this tutorial looks decent to me:
[http://www.ibm.com/developerworks/library/l-gnuplot/](http://www.ibm.com/developerworks/library/l-gnuplot/)

---

### Post by technmom on 2011-04-15
> **rosencrantz said:**
> Did you set a non-X terminal (like ps or png)?
How do I do that?

---

### Post by technmom on 2011-04-15
> **wt8008 said:**
> Please explain in more detail what exactly you did or tried to do to start gnuplot and to plot the sin(x) function.
I installed gnuplot, that may be my problem 
in terminal I typed: gnuplot
then plot sin(x)

I have gnuplot running on my lab computer with Ubuntu and this works just fine. 

I'm thinking I need to unistall it and start over

---

### Post by technmom on 2011-04-15
Okay I used find to find gnuplot and removed it then I reinstalled x11 using
sudo apt-get install gnuplot-x11

I think I had the nox versiont.

It works now

---

