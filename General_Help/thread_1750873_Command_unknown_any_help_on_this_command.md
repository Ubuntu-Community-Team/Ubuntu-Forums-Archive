---
title: "Command unknown any help on this command??"
date: 2011-05-06
forum: General Help
---

### Post by mattintc10 on 2011-05-06
In an article i read i finnaly figured out that having a wired connection works A LOT better than wireless for the time being and using a different laptop. Anyways i am on the last line of this and it says this 

d) sudo gedit /etc/modules [where I added 'ndiswrapper' as the last line to the file and saved it.


What does this mean nothing i do will make it work and i am beyond confused.

---

### Post by kerry_s on 2011-05-06
you must be following some really old guide.

open software center
type-> ndis <- in the search
click-> install

that's it, done. look in your menu & use it to install your windows driver.

---

### Post by mattintc10 on 2011-05-06
> **kerry_s said:**
> you must be following some really old guide.

open software center
type-> ndis <- in the search
click-> install

that's it, done. look in your menu & use it to install your windows driver.

Got all of that done of course with a wired connection. Now i just reboot with the driver installed??

---

### Post by 4Orbs on 2011-05-06
Since you are using Xubuntu, the command should be:
```
gksudo mousepad /etc/modules
```
which will open the file /etc/modules in the text editor (mousepad) with administrative powers, and allow you to add the required line and save it.

EDIT: ooops, my reply was too slow. Please disregard.

---

### Post by mattintc10 on 2011-05-06
> **4Orbs said:**
> Since you are using Xubuntu, the command should be:
```
gksudo mousepad /etc/modules
```which will open the file /etc/modules in the text editor (mousepad) with administrative powers, and allow you to add the required line and save it.

What does this do anyways and what am i suppose to edit out so it will boot the ndiswrapper or what ever on boot up?

---

### Post by kerry_s on 2011-05-06
> **mattintc10 said:**
> Got all of that done of course with a wired connection. Now i just reboot with the driver installed??

yes, if you got the right driver your wireless should work.

---

### Post by mattintc10 on 2011-05-06
> **kerry_s said:**
> yes, if you got the right driver your wireless should work.

My wireless doesnt work for jack and i had to make a new thread even though i hate to multi thread my problem. Cause im going to get some people mad at me.

---

### Post by nothingspecial on 2011-05-06
modules are drivers (sort of)

The file /etc/modules is a list of module to be loaded at boot.

You may need to blacklist the module that normally get's loaded.

Please post a link to what you have read and post the output of

```
lshw -C network
```

---

### Post by kerry_s on 2011-05-06
> **mattintc10 said:**
> My wireless doesnt work for jack and i had to make a new thread even though i hate to multi thread my problem. Cause im going to get some people mad at me.

yeah, i just realized it was you on the other thread. lol
pick 1 & stick with it. :D

---

