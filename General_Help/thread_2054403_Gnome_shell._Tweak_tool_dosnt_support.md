---
title: "Gnome shell. Tweak tool dosnt support ??"
date: 2012-09-07
forum: General Help
---

### Post by dgaa1991 on 2012-09-07
i just installed gnome shell on ubuntu 12.04 LTS but i cant use many of the features in tweak tool. There is a ! and if i hold the mouse over it, it says this expansion don't support the shell version. (somthing like that. i am frmo denmark and that is the reason ubunut is in danish ;) )

what to do ?

---

### Post by cortman on 2012-09-07
How did you install Gnome shell?

---

### Post by Frogs Hair on 2012-09-07
12.04 uses the Gnome Shell 3.4 if installed from the software center so make sure your extensions are compatible.

---

### Post by dgaa1991 on 2012-09-08
i mean this was the way :

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell

*Edit*
My gnome version is :
gnome-session 3.4.2.1

But is there a way to fix it ?

---

### Post by dgaa1991 on 2012-09-09
or is it just a dead end ](*,)

---

### Post by cortman on 2012-09-10
Might need to reinstall the extensions?

```
sudo apt-get install gnome-shell-extensions --reinstall
```

---

### Post by Cheesemill on 2012-09-10
What is happening is that certain extensions you're using aren't compatible with your version of Gnome Shell.

Really the only thing that you can do is to wait for the developers of the extensions to update their code.

---

### Post by dgaa1991 on 2012-09-11
exactly. They arent combatible with my Version of gnome shell



> **Cheesemill said:**
> What is happening is that certain extensions you're using aren't compatible with your version of Gnome Shell.

Really the only thing that you can do is to wait for the developers of the extensions to update their code.

---

