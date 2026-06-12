---
title: "man getting piped into more"
date: 2009-06-30
forum: General Help
---

### Post by gachnar on 2009-06-30
I am new to ubuntu forums and hopefully someone can help me out. I just installed debian lenny and was looking around when I decided to check out the man pages on a few packages. 

long story short, on this system man gets piped into more and doesn't act like I would like. what do I need to do to make man on my system act like that on ubuntu? its really annoying that I can't use the up and down arrows.

I look forward to getting this fixed.:p

---

### Post by decoherence on 2009-06-30
Hi!

First of all, make sure less is installed. You should be able to 'apt-get install less'. If it doesn't work after that, or if it says it's already installed.... well, I guess you want to reconfigure groff but I'm not sure on that. In the mean time, you could do

```
man -P less *programname*
```

hopefully someone has a better answer.... let us know whether less was installed, though, and if not, whether installing it fixed your issue.

tanx!

---

### Post by benj1 on 2009-06-30
i think man uses less to display man pages, and more is just a sym link to less.

if you look in /etc/manpath.config it has a pager option to change to less
or you could sym link more to less.
i also think that pager is linked to less, (less opens when i type pager) which is what man actually uses, i havent looked into it but i assume thats just a link to less which could be changed to point less, i assume this is used like a global variable to modify your prefered browser

---

### Post by decoherence on 2009-06-30
> **benj1 said:**
> i think man uses less to display man pages, and more is just a sym link to less.

if you look in /etc/manpath.config it has a pager option to change to less
or you could sym link more to less.
i also think that pager is linked to less, (less opens when i type pager) which is what man actually uses, i havent looked into it but i assume thats just a link to less which could be changed to point less, i assume this is used like a global variable to modify your prefered browser

Good call! I thought manpath.config was just for assigning the path to man pages, but it also says 

```
#DEFINE         pager   pager -s
```

So if I do the following...

```
$ which pager
  /usr/bin/pager
$ stat /usr/bin/pager
  File: `/usr/bin/pager' -> `/etc/alternatives/pager'
$ stat /etc/alternatives/pager
  File: `/etc/alternatives/pager' -> `/usr/bin/less'
$ sudo rm /etc/alternatives/pager
$ sudo ln -s /bin/more /etc/alternatives/pager
```

Now my manual pages display using 'more' like your system. You should be able to use the same method to assign /etc/alternative/pager to /usr/bin/less (like it is... or was... on my system) with a command like

```
sudo rm /etc/alternatives/pager
sudo ln -s /usr/bin/less /etc/alternatives/pager
```

---

