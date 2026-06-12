---
title: "Terminal Commands"
date: 2011-07-15
forum: General Help
---

### Post by Ha1fDead on 2011-07-15
Hello,

I am a fresh person into linux, and was wondering if there are terminal commands to do a few things such as:

1. lock the computer
2. disable the network card (I tried ifconfig eth1 down, but it didn't work {eth1 WAS my current connection})

I will populate this list with more questions as time goes on. Thank you in advance for your help.

---

### Post by haqking on 2011-07-15
> **Ha1fDead said:**
> Hello,

I am a fresh person into linux, and was wondering if there are terminal commands to do a few things such as:

1. lock the computer
2. disable the network card (I tried ifconfig eth1 down, but it didn't work {eth1 WAS my current connection})

I will populate this list with more questions as time goes on. Thank you in advance for your help.

rather than provide the commands and then keep doing it as you ask the questions i will refer you to the use of a command:

apropos <keyword or words>

for example:

apropos <copy>

will find all commands that may utilise the copy function such as cp to be able to copy files.

It is used to find the command you want to do something even if you dont know if a command exists or what one it is.

then with each command you can read the man pages on the command such as:

man apropos

however to lock screen just type ctrl+alt+l

disable nic then look up iwconfig,ifconfig etc

---

### Post by Ha1fDead on 2011-07-15
So, to find a lock command, I would use apropos lock (in the terminal). And to find out the NIC parts, I would use apropos ifconfig.

---

### Post by haqking on 2011-07-15
> **Ha1fDead said:**
> So, to find a lock command, I would use apropos lock (in the terminal). And to find out the NIC parts, I would use apropos ifconfig.


man apropos

will tell you how to use apropos.

You said you were gonna ask more questions, i am giving you facility to answer your own and learn alot in the process rather than command after command.

here for resources on more general CLI use
[http://linuxcommand.org/](http://linuxcommand.org/)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

and there are lots of resources on how to do system admin using the terminal

there are usually lots of ways to carry out the same task.

gnome-screensaver-command --lock

will lock your screen as lock as Gnome screensaver daemon is working for example.

ifconfig gives you access to NIC information, read the man pages on it

---

### Post by Dbury5 on 2011-07-15
Thanks Haqking, this is my first post but you have helped me out so much without me ever having to directly address you or ask a specific question. 

Thanks again!

---

### Post by Frogs Hair on 2011-07-15
Here is a PDF quick reference and some other useful commands .


[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by drmrgd on 2011-07-15
+1  I just learned another new thing from you that I didn't even know I needed to learn.  Thanks!

---

### Post by haqking on 2011-07-15
> **Dbury5 said:**
> Thanks Haqking, this is my first post but you have helped me out so much without me ever having to directly address you or ask a specific question. 

Thanks again!

no problem, happy learning ;)

---

