---
title: "gnuplot problem"
date: 2009-08-20
forum: General Help
---

### Post by athlonshi on 2009-08-20
Hi,
I just installed gnuplot-x11 and gnuplot-nox
But when I loaded gnuplot-nox, the default terminal is unknown.
I also tried to set terminal but couldn't find X11.
I am pretty sure X11 package is installed on my Ubuntu 9.04.
Can anyone shed some light on this? Thanks!
Yu

---

### Post by tgalati4 on 2009-08-20
sudo apt-get install gnuplot
gnuplot
(within gnuplot)
gnuplot> plot sin(x)

Be amazed.

---

### Post by athlonshi on 2009-08-21
Thanks for your reply!
I tried that and the problem was when I loaded gnuplot, the terminal is unknown and I couldn't find X11 in the list of terminals of gnuplot. 
So when I tried to use plot sin(x),nothing appeared on the screen. 
Yu

---

### Post by tgalati4 on 2009-08-21
On Jaunty, gnuplot shows up with a default terminal wxt 0.

gnuplot> set terminal wxt
gnuplot> show terminal 

   terminal type is wxt 0

---

### Post by athlonshi on 2009-08-21
Thanks!
But wxt is also not one of the listed terminals in my gnuplot or gnuplot-nox
I am not lucky with this. 
When I set terminal wxt, it is not recognised saying"unknown or ambiguous terminal type; type just 'set terminal' for a list"

---

### Post by athlonshi on 2009-08-21
I just reinstalled X11 and uninstalled gnuplot 
Then installed gnuplot again, now the wxt shows as the default terminal finally!

---

