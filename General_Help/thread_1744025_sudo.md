---
title: "sudo"
date: 2011-04-30
forum: General Help
---

### Post by nzashadow on 2011-04-30
E: Type 'sudo' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I am very new to linux, and installed ubuntu 10.10 recently. I have been setting my computer up for the last couple days and I ran into this problem, and I don't know how to solve the problem. 

Anyone know what I could have done to cause this and what I can do to fix it?

Also, going into synaptic package manager I get the error: 

E: Type 'sudo' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by jocko on 2011-04-30
> **nzashadow said:**
> E: Type 'sudo' is not known on line 61 in source list /etc/apt/sources.list
...
You have added something to line 61 of your /etc/apt/sources.list file that does not belong there.
If you post the contents of the file I can tell you what's wrong.

---

### Post by nzashadow on 2011-04-30
what command would I use to see the contents?

---

### Post by jocko on 2011-04-30
Either browse to the file and open it up in gedit, or see it in a terminal:
```
cat /etc/apt/sources.list
```

---

### Post by nzashadow on 2011-04-30
actually I think I see what's wrong, how do I edit it?

---

### Post by jocko on 2011-04-30
You open it in a text editor with admin rights:
```
gksudo gedit/etc/apt/sources.list
```
Or:
```
sudo nano /etc/apt/sources.list
```

---

### Post by nzashadow on 2011-04-30
Thank you! Everything is good, till my next problem :P

---

