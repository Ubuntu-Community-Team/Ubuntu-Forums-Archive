---
title: "Accessing a disk using sudo"
date: 2011-06-25
forum: General Help
---

### Post by Zortis on 2011-06-25
How can I access a disk using the sudo command?

Thx<3 ^_^

---

### Post by TeoBigusGeekus on 2011-06-25
Can you please give us some more info?

---

### Post by haqking on 2011-06-25
> **Zortis said:**
> How can I access a disk using the sudo command?

Thx<3 ^_^

what do you mean ?

each disk is usually a mount point and accessed with a simple command to change directory and so you can use CD /etc/apt for example regardless of the physical disk

be more specific

---

### Post by Zortis on 2011-06-25
Rather than accessing it normally accessing it as sudo.

---

### Post by TeoBigusGeekus on 2011-06-25
The easiest way is to start nautilus with root priviledges
```
gksu nautilus
```
and access the drive from there.

---

### Post by Zortis on 2011-06-25
And nautilus is what?

---

### Post by haqking on 2011-06-25
> **Zortis said:**
> And nautilus is what?

your graphical file manager (like windows explorer) except it dont hang ;-)

---

### Post by TeoBigusGeekus on 2011-06-25
Ubuntu's file manager; the program that starts when you press home, Documents, Music, etc.

---

### Post by -kg- on 2011-06-25
Nautilus is the default file browser for Ubuntu.

---

### Post by Zortis on 2011-06-25
Was this an addition to 11.04 just because I've never heard that mentioned before.

I'm using 10.10.

---

### Post by -kg- on 2011-06-25
No, Nautilus has been in Ubuntu forever.

What exactly is the reason you want to access your partitions (hard drive) using sudo?  Such access can be dangerous in the extreme if you don't know what you're doing.

---

### Post by TeoBigusGeekus on 2011-06-25
No, nautilus is ubuntu's file manager for quite a long time now.

---

### Post by Zortis on 2011-06-25
Let's say using gksu nautilus isn't an option.

Just need to do it with a sudo command and nothing else ^_^

---

### Post by Morbius1 on 2011-06-25
I don't know about anyone else but I find the questions asked on the weekends fascinating. It appears we are in an infinate loop at the moment so let's try this:

Open a terminal and type:
```
sudo su
```You are now in a root terminal. If you want to go to the mount point of a partition then:
```
cd /path/to/partition/mount/point
```Now you are at your destination. What you do there is anyone's guess.

---

### Post by haqking on 2011-06-25
> **Zortis said:**
> Let's say using gksu nautilus isn't an option.

Just need to do it with a sudo command and nothing else ^_^

is it your machine and do you have authorisation to use a sudo account and/or access the disk ? ;-)

if so please do say why gksu nautilus is not an option ?

as much information as possible helps more accurate assitance ;-)

---

### Post by MrMichaelHill on 2011-06-25
sudo nautilus


then just navigate the the required disk?

---

### Post by TeoBigusGeekus on 2011-06-25
> sudo nautilus


 then just navigate the the required disk?
Not sudo with graphical apps:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

