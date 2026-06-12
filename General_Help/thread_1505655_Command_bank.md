---
title: "Command bank"
date: 2010-06-09
forum: General Help
---

### Post by goltoof on 2010-06-09
I've completely switched to Ubuntu, but my way around the command line is still amateur at best. I've been good about storing the ones I use most but it takes some time to remember them all since I don't always use them every day. 

Is there a terminal-based tool that stores commands with a description and quickly copies and pastes them into the command line?

ie, stuff like ```
 /proc/acpi/thermal_zone/THRM$ cat temperature 
```

.bashrc_history, stores everything, but if you haven't used a certain command in a long time you have to wade through tons of history to retreive it, and it's not always clear what each command in your history accomplishes. It'd just be nice to query a command bank with keywords to get to it quicker...

---

### Post by dino99 on 2010-06-09
everytime you run a command into a terminal, the command is stored into .bashrc_history

you can easily refound them with the arrows keys (up & down)

more info with the links below

---

### Post by goltoof on 2010-06-09
> **dino99 said:**
> everytime you run a command into a terminal, the command is stored into .bashrc_history

you can easily refound them with the arrows keys (up & down)

more info with the links below

yep, that's the most predictable response..

but if you haven't used a certain command in a long time you have to wade through tons of history to retreive it, and it's not always clear what each command in your history accomplishes

It'd just be nice to query a command bank with keywords to get to it quicker...

---

### Post by karthick87 on 2010-06-09
It will list all the commands which is executed previously,

```

karthick@Ubuntu-desktop:~$ cat ~/.bash_history

```


Press CTRL+R in terminal and type the command,For example if you you already typed clear in terminal while typing c it retrieves the full command


```
(reverse-i-search)`c': clear
```

---

### Post by goltoof on 2010-06-10
does anyone actually understand what I'm asking for in this post?

---

