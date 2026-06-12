---
title: "Gnome on Ubuntu server"
date: 2011-10-29
forum: General Help
---

### Post by ASH.AT on 2011-10-29
Hey all,

I've a project in my college, it's about configuring the Squid proxy on Ubuntu server, finally, I've decided to use the gnome desktop environment since it's my first time and i'm having so many troubles... 
I installed the gdm earlier using 

```
apt-get install gdm
``` 

of course after i updated the kernel, but it still didn't show a GUI, i heard that it's a matter of file that i need to edit and make the default gdm run

i don't know if should used the command

```
apt-get install gnome-desktop
```
and i don't know the difference between them

i also tried the ```
startx
``` command but it gave me an error.

Any help about the file or how to start the gnome desktop pls :)

---

### Post by tartalo on 2011-10-29
[http://www.linuxquestions.org/questions/linux-newbie-8/gnome-on-ubuntu-server-edition-675193/](http://www.linuxquestions.org/questions/linux-newbie-8/gnome-on-ubuntu-server-edition-675193/)

Anyway, why would anyone want to install Gnome in a server?

---

### Post by haqking on 2011-10-29
```
sudo apt-get install ubuntu-desktop
```

though servers shouldnt run a GUI

---

### Post by ASH.AT on 2011-10-30
> **tartalo said:**
> [http://www.linuxquestions.org/questions/linux-newbie-8/gnome-on-ubuntu-server-edition-675193/](http://www.linuxquestions.org/questions/linux-newbie-8/gnome-on-ubuntu-server-edition-675193/)

Anyway, why would anyone want to install Gnome in a server?

> though servers shouldnt run a GUI


I'm preparing a large project in college, and i've to use all the sources i can get (like using tow different network cards for uploading and downloading links to the server) and i don't want to lose my time searching the net for commands used to do small stuff that's not used in reality :D
i did this:

```
apt-get install update
apt-get install gdm
```

but none is working and the startx command also doesn't work :(

---

### Post by haqking on 2011-10-30
> **ASH.AT said:**
> I'm preparing a large project in college, and i've to use all the sources i can get (like using tow different network cards for uploading and downloading links to the server) and i don't want to lose my time searching the net for commands used to do small stuff that's not used in reality :D
i did this:

```
apt-get install update
apt-get install gdm
```

but none is working and the startx command also doesn't work :(

my post above you tells you the command to install dekstop.

and as for reality, the reality is that on a server CLI is used primarily ;-)

---

### Post by ASH.AT on 2011-10-30
> **haqking said:**
> my post above you tells you the command to install dekstop.

and as for reality, the reality is that on a server CLI is used primarily ;-)

First of all, thank you, i think what you are trying to tell me is that gdm differs from gmone-desktop, so i'm gonna install it.

Second, the whole thing about using GUI is that i've broadband connection to the internet, and i searched a lot for how to configure the broadband from ubuntu server (or from terminal) and i saw some stuff but they were so difficult to do :(

But when using the GUI i'll have more flexibility hopefully...

Thank you again and if you have any ideas to share with me i'll be thankful for you ;)

---

### Post by haqking on 2011-10-30
> **ASH.AT said:**
> First of all, thank you, i think what you are trying to tell me is that gdm differs from gmone-desktop, so i'm gonna install it.

Second, the whole thing about using GUI is that i've broadband connection to the internet, and i searched a lot for how to configure the broadband from ubuntu server (or from terminal) and i saw some stuff but they were so difficult to do :(

But when using the GUI i'll have more flexibility hopefully...

Thank you again and if you have any ideas to share with me i'll be thankful for you ;)
 
GDM is Gnome Display Manager.

Ubuntu-desktop is a package which contains GDM (the login prompt) and many other necessary packages

you need more than just GDM for a fully functional desktop GUI

for example in the latest Ubuntu 11.10, it uses LightDM or LDM as its desktop manager (login) Gnome 3.2 as the DE (desktop environment) and the Unity Shell

---

### Post by collisionystm on 2011-10-30
Don't run gnome

Use lxde

---

### Post by haqking on 2011-10-30
yes collision mentions above there are many alternatives to Gnome

xfce, kde, lxde, fluxbox ad nauseum ad infinitum

It is all choice

---

### Post by ASH.AT on 2011-11-04
ok thanks guys :)

---

