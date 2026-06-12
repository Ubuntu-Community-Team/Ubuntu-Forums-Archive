---
title: "A very simple question"
date: 2010-04-06
forum: General Help
---

### Post by chejose on 2010-04-06
I would like to open the file manager by command line using sudo, but I just can't remember the name of it!! I can "almost" remember it... but it escapes me. And I am afraid I don't know where to look for it.

So I ask.

Thanks,  José

---

### Post by mcduck on 2010-04-06
```
gksudo nautilus
```
..if it's the Gnome's file manager you want to open.

---

### Post by JamezQ on 2010-04-06
nautilus


Just remember nau, then you can simply press tab once or twice and ubuntu will finish the work for you

---

### Post by lisati on 2010-04-06
To open the file manager, use:
```
nautilus
```

For more information on (gk)sudo, see here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2010-04-06
Check out [nautilus-gksu]("apt://nautilus-gksu") (click the apturl link to install it). 

*[I]The gksu extension for nautilus allows you to open files with administration privileges using the context menu when browsing your files with nautilus.*[/I]

You may have to log out and log back in after installing it.

---

### Post by nothingspecial on 2010-04-06
> **chejose said:**
> I would like to open the file manager by command line using sudo, but I just can't remember the name of it!! I can "almost" remember it... but it escapes me. And I am afraid I don't know where to look for it.

So I ask.

Thanks,  José

I`m sure you have a good reason, but, why?

---

### Post by chejose on 2010-04-06
Very good... thanks. Very simple, but not for my memory.

It is one of the easiest ways of changing permission on files. I have done it with chmod in the past, but this is easier.

José

---

### Post by chejose on 2010-04-06
P.S. I would mark this as "solved" but haven't figured out how to do it yet.

---

### Post by lisati on 2010-04-06
> **chejose said:**
> P.S. I would mark this as "solved" but haven't figured out how to do it yet.

At the top of the thread, there's "thread tools". Click on that, and look for "Mark thread as solved"

---

### Post by chejose on 2010-04-06
Thanks... I have wondered about that for some time. It is not very obvious!

José

---

