---
title: "Synaptic Configuration Question"
date: 2005-02-16
forum: General Help
---

### Post by smx on 2005-02-16
When synaptic has started an installation but configuration has to be done before it can be completed, an ncurses window will appear in the Synaptic terminal window with the title "Ubuntu Configuration".

I've looked everywhere but can't find a program with this name. What the *$&% is it? How do I run it from the command line? Hoping it does something useful, as I have some major configuration issues with my installation. 

Need help -- Please! Thanks --  :-P

---

### Post by az on 2005-02-17
dpkg-reconfigure

for example, if you want to reconfigure your Xserver
sudo dpkg-reconfigure xserver-xfree86.


You must run it from the comand line and you must know the name if the package.

---

