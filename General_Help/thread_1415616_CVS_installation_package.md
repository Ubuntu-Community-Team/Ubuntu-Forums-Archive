---
title: "CVS installation package"
date: 2010-02-25
forum: General Help
---

### Post by eawedat on 2010-02-25
hey all
am trying to install cvs on my ubuntu and getting this message:-
 
gnuworld@muhamad-laptop:~$ sudo apt-get install cvs
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package cvs
 
wt to do ? [IMG]http://nixcraft.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by gmargo on 2010-02-25
That's the right package to install, but your software sources must be out of date, or still configured to only load from the CDROM.  Check /etc/apt/sources.list and rerun "apt-get update".  If you're not familiar with the sources.list format you should probably change it the graphical way.

---

### Post by eawedat on 2010-02-25
hey gmargo
thank you very much
you were very helpful
 
it worked 100% :)
i did apt-get update
and then after used cvs :)
 
thanks again.

---

