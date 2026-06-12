---
title: "ubuntu server"
date: 2011-01-16
forum: General Help
---

### Post by gujjerji on 2011-01-16
hello ubuntu users
i was install ubuntu server 
instaltion is complate after that i get black screen they ask to me user and password 
and after i dont know 
i ma new user user of server 
i want to run my media site 
but i cant under stand what i do next 
please any one help me 
thank you

---

### Post by WorMzy on 2011-01-16
Server doesn't come with a desktop environment (GUI).

If you want to learn how to use Ubuntu without a desktop environment, start here: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

If you'd rather just install a desktop environment, log in and run one of the following:

```
sudo apt-get install ubuntu-desktop
#for GNOME
```
```
sudo apt-get install kubuntu-desktop
#for KDE
```
```
sudo apt-get install xubuntu-desktop
#for XFCE
```
```
sudo apt-get install lubuntu-desktop
#for LXDE
```

---

### Post by kellemes on 2011-01-16
Server edition has no Graphical environment.
Somthing to read.. [https://help.ubuntu.com/10.10/serverguide/C/index.html]("https://help.ubuntu.com/10.10/serverguide/C/index.html")

---

### Post by TheHackOps on 2011-01-16
Can i ask why the dev team does not put the ubuntu desktop enviroment onto the server edition...

---

### Post by HermanAB on 2011-01-16
Well, basically, the server edition is for people who already know what they are doing.

If you don't quite know what you are doing, please use regular Ubuntu, the desktop version, with all the blinky lights and mouse thingies.

...and if you really, really, really don't know what you are doing and need clicketywizards for everything, please use OpenSuse.

---

### Post by oldos2er on 2011-01-16
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by jonbonjovi on 2011-01-16
It' a bit difficult to understand you...can you login into the system? can you see the command line:
> username@pcname:
?

---

### Post by overdrank on 2011-01-16
Forum error. Threads merged :)

---

### Post by gujjerji on 2011-01-17
> **jonbonjovi said:**
> It' a bit difficult to understand you...can you login into the system? can you see the command line:
 
?
i can see it 
but after how can i put my site there and how can i edit some think if i want

---

### Post by WorMzy on 2011-01-17
This explains how to get a basic webserver up and running: [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

This explains how to add PHP support to it: [https://help.ubuntu.com/10.04/serverguide/C/php5.html](https://help.ubuntu.com/10.04/serverguide/C/php5.html)

For editing pages: [https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)

---

### Post by pipemartinm on 2011-01-17
From the sound of things you're probably best off starting from scratch with the desktop version [http://www.ubuntulinux.org/desktop](http://www.ubuntulinux.org/desktop). Lots of nice friendly menus for you.

---

### Post by gujjerji on 2011-01-19
> **pipemartinm said:**
> From the sound of things you're probably best off starting from scratch with the desktop version [http://www.ubuntulinux.org/desktop](http://www.ubuntulinux.org/desktop). Lots of nice friendly menus for you.
if i get this one can i run my site with domain ??
can i use ubuntu server like desktop server??

---

