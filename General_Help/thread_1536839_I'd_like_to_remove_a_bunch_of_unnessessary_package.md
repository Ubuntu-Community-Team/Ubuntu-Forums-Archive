---
title: "I'd like to remove a bunch of unnessessary packages"
date: 2010-07-22
forum: General Help
---

### Post by sofasurfer on 2010-07-22
I'd like to remove a bunch of unnessessary packages. Trouble is, I don't know what they all do. Is there a list of packages that tells what is/is not nessessary to run my system? I'm sure there are hundreds of packages (well, maybe tens of packages) that I have no use for but I don't know what they are.

---

### Post by richardjh on 2010-07-22
I think you will struggle to get a good answer to this question.

The problem is how to define *necessary*. 

You could run just the kernel, filesystem, bash and cron but you wont be able to do much.

Only you will know what you can remove. 

For example do you need any graphical interface?
What about a web browser?
Do you need a package manager?

You could start the other way and install Ubuntu Minimal install from the server installation CD and then add packages as you need them. That will keep things pretty trimmed down.

I suppose it all depends on what you are trying to achieve.

For the list you have asked for, look in Synaptic and use the Status view and list only installed packages. You can look down the list and read a description of what each package does and then decide if you want to remove it or not.

---

### Post by bodhi.zazen on 2010-07-22
> **sofasurfer said:**
> I'd like to remove a bunch of unnessessary packages.

OK, do it ...

> Trouble is, I don't know what they all do.

Well, that would be a problem then. In general if you do not know what it is, do not remove it.

> Is there a list of packages that tells what is/is not nessessary to run my system? I'm sure there are hundreds of packages (well, maybe tens of packages) that I have no use for but I don't know what they are.

I suggest you perform a minimal install and build up.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If you want the bar bones minimum, use debootstrap. Install Ubuntu in a chroot and generate a list of installed packages.

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

There are a few packages you can remove from the minimal / deboostrap if you like.

Here is a starting point for packages :

[http://packages.ubuntu.com/lucid/ubuntu-minimal](http://packages.ubuntu.com/lucid/ubuntu-minimal)

---

### Post by tgm4883 on 2010-07-22
> **sofasurfer said:**
> I'd like to remove a bunch of unnessessary packages. Trouble is, I don't know what they all do. Is there a list of packages that tells what is/is not nessessary to run my system? I'm sure there are hundreds of packages (well, maybe tens of packages) that I have no use for but I don't know what they are.

How do you know they are unnecessary if you don't know what they are? 


*Waves hand in front of face* 
These are not the packages you are looking for.

---

### Post by Goolie on 2010-07-22
touche. . .

---

