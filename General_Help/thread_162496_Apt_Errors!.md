---
title: "Apt Errors!"
date: 2006-04-19
forum: General Help
---

### Post by chris062689 on 2006-04-19
From another post down below,
"Convert from KDE to Gnome"
It told me to 

sudo apt-get update
sudo apt-get install ubuntu-desktop

But, I get this error:
chris@chris:~$ sudo apt-get update
Password:
E: Malformed line 1 in source list /etc/apt/sources.list (dist parse)

I also know that I cannot access the adept package manager or the adapt updater; I get this error when I try to access them.

The APT Database could not be opened!  This may be caused by incorrect APT configuration or something similar.  Try running apt-setup and apt-get update in the terminal and see if that helps to resolve the problem.

---

### Post by localzuk on 2006-04-19
You need to take a look at the /etc/apt/sources.list file (sudo gedit /etc/apt/sources.list) and take a look at line 1 - which it states is 'malformed'. Compare it to other sources.list files on here (do a search for sources.list and see).

---

### Post by gingermark on 2006-04-19
[QUOTE=localzuk]sudo gedit /etc/apt/sources.lis.[/QUOTE]
```
kdesu kate /etc/apt/sources.list
``` in Kubuntu.

---

