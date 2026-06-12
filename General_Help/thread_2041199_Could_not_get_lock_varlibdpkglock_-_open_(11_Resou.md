---
title: "Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)"
date: 2012-08-12
forum: General Help
---

### Post by mejbr2003 on 2012-08-12
help
trying to install gnome
cant download it
it's asking if another process is usiing it

What did I do?

---

### Post by plucky on 2012-08-12
> **mejbr2003 said:**
> help
trying to install gnome
cant download it
it's asking if another process is usiing it

What did I do?

Do you have more than one package manager open at the same time?

Package Managers are **apt-get,synaptic,update-manager,Software-Center** etc.

---

### Post by mejbr2003 on 2012-08-12
no i dont
thanks

---

### Post by mejbr2003 on 2012-08-12
is there a way to end the apt process?
im seeing that other peoplle have problems ttf thing as well

---

### Post by johnathansmith on 2012-08-12
> **mejbr2003 said:**
> is there a way to end the apt process?
im seeing that other peoplle have problems ttf thing as well


> If you ever encounter a failure with apt-get, perform the operations on a console under root:
Kill the process named apt-get: killall -9 apt-get
Reconfigure dpkg: dpkg --configure -a
Update apt-get: apt-get update
Update packages, including improperly installed: apt-get upgrade

[source]("http://en.kioskea.net/faq/810-unblocking-apt-get")

---

### Post by ljube on 2013-06-12
well,..seems like johnathansmith's post is fine. Just missing the sudo :)
For me it worked like this:

sudo -i killall -9 apt-get

 sudo dpkg --configure -a

 sudo apt-get update

sudo apt-get upgrade

So I guess would be the final solution.Thank you for posting the problem :)

---

### Post by HiImTye on 2013-06-12
you should use```
sudo apt-get dist-upgrade
```instead of```
sudo apt-get upgrade
```so you don't end up with a partially installed update

but I'm glad you got it sorted out. here's a good one liner to fix the error in the future
```
procs="apt-get update-manager synaptic aptitude dpkg"; sudo killall "$procs"; sleep 2; sudo killall -9 "$procs"; unset procs; sudo rm -f /var/lib/dpkg/lock; sudo dpkg --configure -a; sudo apt-get update; sudo apt-get dist-upgrade -y
```


[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

