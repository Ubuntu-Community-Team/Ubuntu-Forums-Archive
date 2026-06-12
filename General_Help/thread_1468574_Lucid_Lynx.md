---
title: "Lucid Lynx"
date: 2010-05-01
forum: General Help
---

### Post by ankit.vader on 2010-05-01
To Run boot-time scripts in parallel this is what I did in 9.10 

gksu gedit /etc/init.d/rc

then changed CONCURRENCY=none to CONCURRENCY=shell

How can i do this in 10.04

Also how can i make title bar as it was earlier, that is 'close', 'maximise' options on right??

---

### Post by eltonw on 2010-05-01
> **ankit.vader said:**
> To Run boot-time scripts in parallel this is what I did in 9.10 

gksu gedit /etc/init.d/rc

then changed CONCURRENCY=none to CONCURRENCY=shell

How can i do this in 10.04

Also how can i make title bar as it was earlier, that is 'close', 'maximise' options on right??

[COLOR="DarkRed"][FONT="Century Gothic"][SIZE="2"]LUCID (10.4) Post-installation configuration HELP [/SIZE][/FONT][/COLOR]can be found HERE:
[http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide]("http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide")

---

### Post by ankit.vader on 2010-05-01
> LUCID (10.4) Post-installation configuration HELP can be found HERE:
[http://www.my-guides.net/en/guides/l...allation-guide](http://www.my-guides.net/en/guides/l...allation-guide)

its not given there

---

### Post by ankit.vader on 2010-05-01
any help guys......i cant find it any where

---

### Post by DeMus on 2010-05-01
> **ankit.vader said:**
> any help guys......i cant find it any where

Do the same as before, that's what I did.

---

### Post by Pjotr123 on 2010-05-01
Moving the buttons:
[http://sites.google.com/site/easylinuxtipsproject/tips#TOC-Move-the-window-buttons-to-the-righ](http://sites.google.com/site/easylinuxtipsproject/tips#TOC-Move-the-window-buttons-to-the-righ)

---

### Post by BrockStrongo on 2010-05-01
Also how can i make title bar as it was earlier, that is 'close', 'maximise' options on right??[/QUOTE]
 
 
alt+f2
gconf-editor
apps
metacity
general
button layout
------------> edit value  (by double clicking)
       menu:maximize,minimize,close
 
that should work

---

### Post by ankit.vader on 2010-05-01
ok, i found the button layout, and changed that to windows style, but i still did'nt find anything regarding concurrency modification to run boot time script in parallel

---

### Post by wangsuda on 2010-05-09
> **BrockStrongo said:**
> Also how can i make title bar as it was earlier, that is 'close', 'maximise' options on right??
 
 
alt+f2
gconf-editor
apps
metacity
general
button layout
------------> edit value  (by double clicking)
       menu:maximize,minimize,close
 
that should work[/QUOTE]And it does! thank you for this post!

---

### Post by 3rdalbum on 2010-05-09
> **ankit.vader said:**
> To Run boot-time scripts in parallel this is what I did in 9.10 

gksu gedit /etc/init.d/rc

then changed CONCURRENCY=none to CONCURRENCY=shell

How can i do this in 10.04

The same way. I don't actually think this will give any performance improvements anymore as Ubuntus 9.10 and 10.04 use Upstart, which already has concurrency and probably ignores that file.

---

