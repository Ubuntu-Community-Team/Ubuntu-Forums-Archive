---
title: "Dell XPS M1530 intel 3945 abg wifi chipset not loading properly on 10.04 at startup"
date: 2011-09-21
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-09-21
Hello, 
I've been lookinbg around this whole month trying to solve this problem, but couldn't find an aproppiate answer. I had to reinstall the OS, but before that I had been able to work it out, somehow I don't remember or saved the way to do it, so it's my fault. 
I think many other people are having the same trouble, as I found many posts around the web with quite a frustating feeling gushing from them.
Thank you

---

### Post by &gt;hankim&lt; on 2011-09-21
**up**

---

### Post by &gt;hankim&lt; on 2011-09-21
**Ok here it says that installing these **[B]linux-backports-modules-hardy-generic  packets, with the last version of iwl, it should work just fine but  there's just no way I can find the ones for lucid... 

[/B][B][http://www.cesarsandrigo.com.ar/2008/05/15/dell-xps-m1530-y-linux/](http://www.cesarsandrigo.com.ar/2008/05/15/dell-xps-m1530-y-linux/) 

[/B][B]any hint? 
thx [/B]

---

### Post by &gt;hankim&lt; on 2011-09-21
up

---

### Post by &gt;hankim&lt; on 2011-09-22
up

---

### Post by &gt;hankim&lt; on 2011-09-25
up

---

### Post by &gt;hankim&lt; on 2011-09-25
ok that seemed to have worked!!! at last!!!

on a terminal:

sudo apt-get install linux-backports-modules-wireless-lucid-generic

---

