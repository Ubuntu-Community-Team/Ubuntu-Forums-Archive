---
title: "Opening Applications in Terminal"
date: 2010-08-20
forum: General Help
---

### Post by Ubu-freak on 2010-08-20
I use terminal a lot. Sometimes I would like to open up applications, like start reading a pdf. But when I do 
```

$ evince foo.pdf

```(actually I use zathura to read pdfs now ;), but anyway...)
It opens fine, it's just that that I won't be able to continue using that terminal because it will be waiting for whatever program I just opened to exit. And since I do not want to open new tabs, create new terminal windows, etc (because that's just messy), I am forced to open it like
```
$ nautilus ./
```and then use the GUI to open it. I was wondering if there was any way to open up a pdf and still be able to use the same terminal NOT using the GUI.

---

### Post by Vaphell on 2010-08-20
use & at the end which means 'run in background' for example
nautilus ~ &
or evince something.pdf &

---

### Post by sharathcshekhar on 2010-08-20
Try 
```

$ evince foo &

```

Giving "&" after giving a command will force it to run in Background. So you can use the terminal..

---

### Post by Ubu-freak on 2010-08-20
thanks you guys!

---

### Post by robbiemacg on 2010-08-20
Maybe you're already familiar, but if you're running applications from terminal, you might also want to familiarize yourself with the different ways to list/control/kill processes.

[http://linuxcommand.org/lts0080.php](http://linuxcommand.org/lts0080.php)

---

### Post by silverglade00 on 2010-08-20
You can also chain commands together with &&. This will make the second command start after the first one ends.

"sudo apt-get update && sudo apt-get upgrade" will get you all updated, for example.

---

### Post by Bonster on 2010-08-20
on gnome:

> $ gnome-open anyfile

make it faster by setting it with an alias

> alias g='gnome-open'

so now use

$ g anyfile

---

