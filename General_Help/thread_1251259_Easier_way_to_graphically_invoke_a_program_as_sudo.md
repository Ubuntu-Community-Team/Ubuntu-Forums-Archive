---
title: "Easier way to graphically invoke a program as sudo besides gksudo from a prompt?"
date: 2009-08-27
forum: General Help
---

### Post by nwbnt on 2009-08-27
Rather than typing Alt+F2 and then typing "gksudo ...", is there an easier way to invoke something in Ubuntu/Gnome as sudo? Perhaps some key combo when you left click, or something? If not, any idea on how to create it? thx

---

### Post by TheNosh on 2009-08-27
if i recall properly theres a package called something like "gksu-nautilus" that will let you right click things and select "open as administrator" though thats not useful for starting things from the panel or menu.

---

### Post by michy99 on 2009-08-27
If there is a program you often need to run as root, make a launcher using gksudo with the command.

---

### Post by TheNosh on 2009-08-27
> **michy99 said:**
> If there is a program you often need to run as root, make a launcher using gksudo with the command.

that too (don't know why i didn't think of it)

---

### Post by Gen2ly on 2009-08-27
I always have a terminal open (you can check out drop-down terminals if you want [they're pretty cool]) and then have an alias sudo programs I use frequently in my ~/.bashrc:

```
alias gesu="sudo gedit"
```

---

### Post by nwbnt on 2009-08-27
Out of curiousity, why doesn't ubuntu have a right-click menu popup like Windows does when you right-click on something in a menu? It's usefull not only to have shortcut for invoking the program as administrator, but also for viewing properties, seeing what command will actually be invoked when you left click on it. I think it would be nice if menu items popped up a similar menu as desktop quick launch items do when you right-click on them.

---

