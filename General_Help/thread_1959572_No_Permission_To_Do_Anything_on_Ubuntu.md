---
title: "No Permission To Do Anything on Ubuntu"
date: 2012-04-16
forum: General Help
---

### Post by olakunle on 2012-04-16
I formatted my system a while ago, removing Ubuntu from it cos it was having problems with my wireless at home. I installed Windows back and dont seem to have any problem.
However, I wanted to still have Ubuntu there also, so I installed Ubuntu Linux from Windows 7 using wubi, when I finished the installation, I restarted and was getting errors regarding something about file or disk or something... can't remember.
 
The main problem is though, when I log into Ubuntu, I can't do anything administrative there even though I'm the root user. 
Is it because the ubuntu is on the C: drive and there is some permission issue?

---

### Post by nomanfayez on 2012-04-16
It is so confusing .. There is no Drive consept for Linux.
 
Did you try to use command by "sudo -s" then your user password
it will make you root user.... try "ls -l" and then find the details permission level of your different files and directory on "/" and your "/home/your user name" ......

---

### Post by olakunle on 2012-04-16
so you mean my being even running under C: in Windows (i.e. via Wubi) i should still be able to do whatever I want on Linux? 
 
I'll give ur suggestions a try and report back

---

### Post by mcduck on 2012-04-16
> **olakunle said:**
> so you mean my being even running under C: in Windows (i.e. via Wubi) i should still be able to do whatever I want on Linux? 
 
I'll give ur suggestions a try and report back

Yes, Ubuntu uses it's own filesystem, which just happens to be located inside the Windows filesystem instead of a separate partition if you make a Wubi install. It should perform pretty much exactly the same as a regular install and allow you to do all the same things.

The most likely reason (and also the explanation and a way to solve the problem) is the error messages about "a drive or disk or something" you got. Getting the exact error message would really, really help a lot in solving this.

(and also since you are new to Ubuntu, and might not be familiar with it's security model, this article might be worth a read: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo"))

---

### Post by mastablasta on 2012-04-16
> **olakunle said:**
> so you mean my being even running under C: in Windows (i.e. via Wubi) i should still be able to do whatever I want on Linux? 
 
 
yes. you need to use sudo (or gksu for GUI) to do administrative tasks.
 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by olakunle on 2012-04-16
I have no idea what happened, but it all seems to be working fine and I can do all the admin stuff I need to do ... probably put in the wrong password :lolflag: 
anyways, anytime I boot up Ubuntu, it says "NTFS File System : 'prefix' not found" before showing the start screen...
This does not affect the performance though..

Thanks a lot guys

---

