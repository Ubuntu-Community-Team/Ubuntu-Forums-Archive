---
title: "script at start up"
date: 2010-02-19
forum: General Help
---

### Post by dapim on 2010-02-19
Hi guys,

Need in start up to activate eth0 , i put it in init.d ,
the problem is that i need root acess to make it work
ifconfig auto eth0 up   
how can i include this in init.d is i need root previlegies to make in run?

---

### Post by ajgreeny on 2010-02-19
Add the commands to the file **/etc/rc.local** (without the need of sudo).  There are a few posts about that not always working, and sometimes depending on a sleep option before the command of a few seconds, ```
sleep 10; command
```but try without first and you may not need the sleep time.

---

### Post by lost_soul on 2010-02-19
How did you put it in init.d ? 
My advise make a type of script.. 
meaning open a file editor of your choice .. 
in the file type : "ifconfig eth0 up" 
and then save to whatever name you want.
Then from the terminal CD to the directory containing the file .. 
chmod +x the file 
then mv "the file" /etc/init.d/
and then in the terminal update rc.d
that should work flawlessly.

---

