---
title: "linux-headers uname -r couldn't be found"
date: 2010-03-16
forum: General Help
---

### Post by michaelfragug on 2010-03-16
**hey guys.**
 
I have rented at VPS in Germany, and I'm trying to install an Asterisk server on it.
But i have a little problem.
 
I'm following this guide. [http://www.ideaglu.net/?p=1150](http://www.ideaglu.net/?p=1150)
And there is a lot of things a have to install.
 
When i try to do this it fails
 
[COLOR=#666699]sudo apt-get install linux-headers-$(uname -r)[/COLOR]
 
[COLOR=#666699]The server replyes: [/COLOR]
 
```
[EMAIL="root@3230"]root@3230[/EMAIL][EMAIL="root@3230"]:~# apt-get install linux-headers-$(uname -a)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-Linux
[/EMAIL]
```
 
[COLOR=#666699]And if type "uname -r" it reply this:[/COLOR]
 
```
[EMAIL="root@3230"]root@3230[/EMAIL][EMAIL="root@3230"]:~# uname -a
Linux 3230.virtual.yourshelter.net 2.6.18-028stab062.3-ent #1 SMP Thu Mar 26 15:12:05 MSK 2009 i686 GNU/Linux[/EMAIL]
```
 
[COLOR=#666699]What am i doing wrong.[/COLOR]
 
[COLOR=#666699]i hope someone can help me.[/COLOR]
 
[COLOR=#666699]Best Regards[/COLOR]
 
[COLOR=#666699]Michael Pedersen, Denmark[/COLOR]

---

### Post by mcduck on 2010-03-16
The guide tells you to run this:
```
sudo apt-get install linux-headers-$(uname -r)
```

...but you are running this instead:
```
sudo apt-get install linux-headers-$(uname -a)
```

(note the **-r** versus **-a**)

---

### Post by michaelfragug on 2010-03-16
I have tryed both methods, but it dosen't help.
Any ideas?

---

### Post by rnerwein on 2010-03-16
hi
i think you are missing something:
[B][COLOR=#666699]sudo apt-get install linux-headers-$(uname -r)[COLOR=Red] build-essential[/COLOR]
[/COLOR][/B]ciao

---

### Post by prodigy_ on 2010-03-16
Seems your **uname** doesn't works properly with **-r** option. Try this workaround: 

```
sudo apt-get install linux-headers-$(uname -a|awk '{ print $3 }')
```

---

### Post by michaelfragug on 2010-03-16
**[COLOR=#666699]If i type:[/COLOR]**
**[COLOR=#666699]"sudo apt-get install linux-headers-$(uname -r)[/COLOR][COLOR=red] build-essential"[/COLOR]**
 
```
 
 
[EMAIL="root@3230"]root@3230[/EMAIL]:~# sudo apt-get install linux-headers-$(uname -r) build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-2.6.18-028stab062.3-ent
 

```
 
And if i type:
 
**sudo apt-get install linux-headers-$(uname -a|awk '{ print $3 }')**
 
```
[EMAIL="root@3230"]root@3230[/EMAIL]:~# sudo apt-get install linux-headers-$(uname -a|awk '{ print $3 }')
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-2.6.18-028stab062.3-ent

```

---

### Post by prodigy_ on 2010-03-16
Means this package doesn't exist in any repository enabled for your system. Which leads to a question: where did you get your current kernel from? ;-)

---

### Post by falconindy on 2010-03-16
> **prodigy_ said:**
> Means this package doesn't exist in any repository enabled for your system. Which leads to a question: where did you get your current kernel from? ;-)
> **michaelfragug said:**
> I have rented at VPS
Tada. Headers are generated at compile time. If you can get your hands on the .config used to make the kernel, you could probably generate them yourself. See if /proc/config.gz exists (it probably doesn't). When it doesn't, you'll probably need to compile your own kernel from scratch.

---

