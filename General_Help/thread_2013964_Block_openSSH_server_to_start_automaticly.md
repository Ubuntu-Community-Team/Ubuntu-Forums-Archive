---
title: "Block openSSH server to start automaticly"
date: 2012-07-01
forum: General Help
---

### Post by LeftFoot on 2012-07-01
Hi there,

I installed openSSH server but do NOT want it to start at each startup.

What is the recommended way to do this ?

-Just delete /etc/init/ssh.conf ?
-Delete the line "start on..." in /etc/init/ssh.conf ?

Something else ?

Thx for any help

LeftFoot

---

### Post by ratcheer on 2012-07-01
The best way would be to comment out the "start on" statement in Upstart.

[http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting](http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting)

Tim

---

### Post by raja.genupula on 2012-07-01
[http://askubuntu.com/questions/56753/how-do-i-disable-ssh-from-starting-automatically-on-10-04](http://askubuntu.com/questions/56753/how-do-i-disable-ssh-from-starting-automatically-on-10-04)

---

### Post by LeftFoot on 2012-07-01
Hey Tim,

So just a # in front of the line, right ?

Thx a LOT :)

Have a great one

LeftFoot

---

### Post by LeftFoot on 2012-07-01
ok, this is it.

Thx Raja and Tim !

LeftFoot

---

