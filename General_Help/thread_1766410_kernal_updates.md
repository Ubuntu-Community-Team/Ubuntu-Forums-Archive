---
title: "kernal updates"
date: 2011-05-24
forum: General Help
---

### Post by flipper T on 2011-05-24
just noticed that i haven't had any kernal updates since installing 11.04

current kernal is 2.6.38-9-generic

is this up to date ?

if not, how to rectify ?

---

### Post by matt_symes on 2011-05-24
Hi

Open a terminal and type..

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen. This is normal.

```
apt-cache search linux-image-2.6.38
```

This will display a list of kernel available on the command line. 

You can also check using synaptic and see what kernels are in the repos.

Check to see if you have the newest one.

Kind regards

---

### Post by snowpine on 2011-05-24
You can always check the current version of any package at packages.ubuntu.com.

[http://packages.ubuntu.com/natty/linux-image](http://packages.ubuntu.com/natty/linux-image)

Kernel updates are applied with the rest of your updates when you run the Update Manager or (if you prefer the terminal):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by satanselbow on 2011-05-24
I'm only on 2.6.38-8.42 on my Gnome3 Natty so if anyone is missing out... grumble... grumble... :D

---

### Post by flipper T on 2011-05-24
thx all

i seem to be up to date, or enough for me at least

when using 10.04 / 10.10 it seemed like there was a new kernal each week

---

### Post by idoitprone on 2011-05-24
[http://kerneltrap.org/Linux/Kernel_Release_Numbering_Redux](http://kerneltrap.org/Linux/Kernel_Release_Numbering_Redux)
[http://www.linfo.org/kernel_version_numbering.html](http://www.linfo.org/kernel_version_numbering.html)

[http://www.linux.com/learn/tutorials/387494:understanding-the-stable-linux-kernel](http://www.linux.com/learn/tutorials/387494:understanding-the-stable-linux-kernel)

not really, the must be minor patches to the kernel. Here is some reading material

---

