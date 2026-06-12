---
title: "Removing bloat from Ubuntu?"
date: 2010-12-19
forum: General Help
---

### Post by wearetheborg on 2010-12-19
First time Ubuntu user (used to be on debian earlier).

I like that everything works out of the box (had to install codecs etc,  but thats standard); but I dont like that there are 260 processes  running. Is there a utility to stop unnecessary processes from running  in Ubuntu 10.10? I used rcconf but there did not seem to be a whole lot  of startup processes that were enabled. Yet somehow I am running 260  processes now.

Even if I log into fluxbox, I get 200+ processes running.

---

### Post by PhantmKllr on 2010-12-19
Ubuntu is just bloaty like that. There's pretty much nothing you can do about it. Sorry

---

### Post by wilee-nilee on 2010-12-19
The processes are sleeping that's not bloat your just copying somebody else's idea.;)
[ATTACH]178913[/ATTACH]


Look at the ram used and the cpu.

---

### Post by jim_deadlock on 2010-12-19
You can go to System -> Preferences -> Startup Apps and disable some of that stuff. Won't make a huge difference but might give you a little satisfaction :)

---

### Post by wi0 on 2010-12-19
One of the first things I would do on a new windows install is prevent a whole bunch of services and applications from starting. On the one hand I would like to do the same in Ubuntu, on the other I don't have enough knowledge, and it works well enough as it is. Then again, windows was running ok too, and it's not like I did any measurements to see if there was improvement.  Is it possible that we're more accepting of some things in linux than we are in windows world?

---

### Post by WorMzy on 2010-12-19
If you want a bloat-free Linux operating system, stay away from Ubuntu. Maybe try Arch or Gentoo.

---

### Post by Vistro on 2010-12-19
Woah woah woah I moved AWAY from Windoze because I wanted less bloat! I will say Linux is one f*** of a lot faster, but I'm with OP on this one... It might just be a nerdy quark, but I'm interested in a bare bones system with nothing but the kernel, networking, and a window manager, then I'll pimp it out from there.

I mean I could go to another distro, but Ubuntu is so well supported (really my only excuse to still use it when somebody says that Ubuntu isn't really Linux, merely because it isn't a pain in the *** to use) that using any other distro would be a nightmare. 

Is there any way to start UNinstalling things until it stops working?

---

### Post by matt-fender on 2010-12-19
After a fresh install, i tend to just go through Ubuntu Software Centre and remove any programs i don't want / never will use.

For example i see some people have 2 messengers, or two bittorent clients, they only ever use one?

Just removing a few programs and editing my startup lists to remove things i won't use.. bluetooth for example. Keeps my distro bloat free :D


EDIT: I think if you remove packages from the package manager they even tell you dependencies, gives you an idea of what needs what to function too

---

### Post by Vistro on 2010-12-19
Is the software center a replacement for Synaptic or are there things that Synaptic shows that software center does not?

Really I want to do just that but have everything marked if deleting it screws up other things.

---

### Post by dummy910 on 2010-12-19
sudo apt-get install bum

then type bum as root in a terminal... pretty self explanatory from there. any help needed, just holler back here hombre'

---

### Post by Vistro on 2010-12-19
Does bum control things that happen during boot or after logon?

---

### Post by wearetheborg on 2010-12-19
> **dummy910 said:**
> sudo apt-get install bum

then type bum as root in a terminal... pretty self explanatory from there. any help needed, just holler back here hombre'


I used bum, seemed to be just the graphical version of rcconf.
I'm not sure bum/rcconf are giving reasonable control. They do not show a lot of processes as being started on boot. In fact they do not even show gdm as being started on boot   :confused:

---

### Post by wearetheborg on 2010-12-19
> **Vistro said:**
> 
Is there any way to start UNinstalling things until it stops working?

I actually dont want to uninstall; I would rather just disable some unnecessary services. Installed but not running processes have no impact, other than they use some hard disk space, but whats an extra GB of hard disk space these days?
Linux is not like Windows with its registry bloating problem ;)

---

