---
title: "Kill background jobs in ubuntu"
date: 2011-05-05
forum: General Help
---

### Post by black_cat on 2011-05-05
Does anyone know how to kill background jobs in ubuntu...???
In Fedora I use "kill %<number jobs>
Ubuntu can use that command and show me some warning "operation not permitted":confused:

---

### Post by cymbaline42 on 2011-05-06
Bunch of ways to do this.  


[LIST=1]
[*]Open System Monitor from System - Administration - System Monitor.  Right click on the process and choose kill.
[*]If a process isn't responding, type Alt + F2 to bring up a box, type "xkill" , the mouse cursor changes to an "x" , click on the process you want to kill.  You can also add the Force Quit button to a toolbar.
[/LIST]

---

### Post by TheNessus on 2011-05-06
> **cymbaline42 said:**
> Bunch of ways to do this.  


[LIST=1]
You can also add the Force Quit button to a toolbar.
[/LIST]
not on 11.04

---

### Post by NightwishFan on 2011-05-06
You can in the classic desktop. :rolleyes:

If you get operation not permitted it means you are trying to kill a process owned by root. You need to add "sudo" in front of it. Though I would not kill tasks owned by the system unless you know it is safe.

---

### Post by black_cat on 2011-05-06
> **NightwishFan said:**
> You can in the classic desktop. :rolleyes:

If you get operation not permitted it means you are trying to kill a process owned by root. You need to add "sudo" in front of it. Though I would not kill tasks owned by the system unless you know it is safe.


Ok, I get it.
But after I login as root still have error....:(
warning like this "ERROR: garbage process ID "%2"

---

### Post by NightwishFan on 2011-05-06
You dont "login as root" just use sudo.

---

### Post by trollger on 2011-05-06
you can type in 

ps -A | more

at the terminal and then kill a process with the kill command

---

### Post by black_cat on 2011-07-11
sudo kill -9 %<jobs number>
or
sudo kill -9 <PID>



Thanks all [Solved] :)

---

