---
title: "Scrolling inside &quot;top&quot; command?"
date: 2006-06-16
forum: General Help
---

### Post by Peepsalot on 2006-06-16
I have a question about the console command "top", which displays a list of processes.
I'd like to know if there is a key to be able to move up or down this list or to page through it somehow, since there are usually more commands running than can fit on the 25 line screen.

If not, could anyone tell me where I would find the source code for this command?

---

### Post by aysiu on 2006-06-17
Well, I read the entire man page for top all the way through, and I think I can confidently say, "No, there's no way to scroll."

What you can do, though, is sort. Press F and then select the letter of the column you want to sort by. Otherwise, just install Gnome's System Monitor.

**Edit**: Whoops. I guess F just gets rid of certain columns. There's something that sorts. I just forget what it is.

---

### Post by maskd on 2006-06-17
sometimes when i have troubles with x server or anything i use top, it seems that when i pressed A (shift + a), it sorted them somehow, and i could see the programs "i" was using (the ones that i was interacting with [firefox, totem, xorg, etc]).

---

### Post by firetux on 2006-06-17
Add "| less" to the command you want to be able to scroll in.

Hmm, it doesn't give a pretty result with me, anyway this is the way you should do it.

---

### Post by aysiu on 2006-06-17
[QUOTE=firetux]Add "| less" to the command you want to be able to scroll in.

Hmm, it doesn't give a pretty result with me, anyway this is the way you should do it.[/QUOTE]
This is what I get when I type ```
top | less
``` > Hmm, it doesn't give a pretty result with me, anyway this is the way you should do it. I'll say!

---

### Post by David Corrales on 2006-06-17
Why don't you try **htop**? It's got a lot more options than top, it's color coded and you can scroll :p
Browse for it on synaptic and enjoy!

---

### Post by guzerat on 2006-06-17
[QUOTE=David Corrales]Why don't you try **htop**? It's got a lot more options than top, it's color coded and you can scroll :p
Browse for it on synaptic and enjoy![/QUOTE]

yup. htop is the way to go

---

### Post by Ramses de Norre on 2006-06-17
htop shows 4 amarok processes, 6 mysqld processes and so on where top only shows one of each.. This is quite confusing.

---

### Post by aysiu on 2006-06-17
Is *htop* an application you have to install? ```
 htop
bash: htop: command not found
```

---

### Post by Peepsalot on 2006-06-17
[QUOTE=David Corrales]Why don't you try **htop**? It's got a lot more options than top, it's color coded and you can scroll :p
Browse for it on synaptic and enjoy![/QUOTE]
Yeah this is just what I had in mind, and more.  Very Nice program.  I'm almost a little disappointed there's no need for me to try me hand at coding one.  I was about to try to write my own version called "bottom"(along the lines of less vs more). :D 
[QUOTE=aysiu]Is *htop* an application you have to install? ```
 htop
bash: htop: command not found
```[/QUOTE]
yep, I found it in synaptic like David suggested, but I think ```
sudo apt-get install htop
``` should work just as well.

---

### Post by David Corrales on 2006-06-17
[QUOTE=Ramses de Norre]htop shows 4 amarok processes, 6 mysqld processes and so on where top only shows one of each.. This is quite confusing.[/QUOTE]
This is because those processes spawn forks or copies of themselves that share resources. You should see them as a single "program" running.
The memory is not cummulative, so if you see 6 mysqld processes that take 20 megs each, it's actually 20 megs for all of them.

---

### Post by Peepsalot on 2006-06-18
[QUOTE=firetux]Add "| less" to the command you want to be able to scroll in.

Hmm, it doesn't give a pretty result with me, anyway this is the way you should do it.[/QUOTE]
Never thought I'd say it , but I don't like the topless look :p

---

