---
title: "Planning a Server..."
date: 2010-05-04
forum: General Help
---

### Post by KriisCDW on 2010-05-04
I'm going to be building an AMD computer soon...

What I plan on doing is Ubuntu Server of some flavor... and using VM's for Ubuntu GUI, 7 and possibly OSX. 

Ultimately I'd like to have dual-monitor support (7 on one screen... Ubuntu or OSx on the other), CPU control (Give each CPU it's own core), good 

Anything I should look out for ahead of time? or any advice from anyone who has done something similar?

As a student who is trying to experiment in multiple areas of expertise, I'd want OS and programming environments to play around with - and security and backup options that VM's give.

Greatly appreciated any advice :)

---

### Post by cariboo on 2010-05-04
The server doesn't have a gui by default, so if you need a gui, and are using the system for most everything, I would suggest installing the desktop version. Btw, OSX will not run in a virtual machine, and according to Apples EULA should only be installed on Apple branded computer systems.

---

### Post by ironic.demise on 2010-05-05
There IS a way to install the GUI on the server by running and apt-get command, 

This should install the desktop onto a server 
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

Mac's *can* be VM'd but as of exactly how I'm not sure as I think it's only VMWare that can do it (Sorry if I'm waaaaaaaaay off on what you want from VM or what you are using)

No idea on CPUs

but note that OSX should **not** be run on anything that isn't MAC hardware, it's as far as I know... illegal and difficult because of MACs having a internal hardware unique to MACs that verify's the hardware and a lot of things go through it before running. you will NOT be able to truly "experiment" on a MAC without the hardware!

7 should be easy on VMWare, or any of the other VMs but I suggest adding XP to your list, it's still worth experimenting with and getting to grips with, a lot of people use it and it has some capabilities that 7 doesn't doesn't hurt any... right?.

Why is this going to be a server?
and agree with cariboo... if you do everything on this "server" then I suggest the desktop version and just install whatever server components you need.

---

