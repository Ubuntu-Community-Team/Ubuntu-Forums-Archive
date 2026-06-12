---
title: "problem - login screen over and over again!!"
date: 2010-12-28
forum: General Help
---

### Post by vievgart on 2010-12-28
hello, 
 
On the login screen, I put my user and password, normal, then a black screen appears for a second, like the session is about to start...
 
but then it comes back again to the login screen...I make login again and it happens the same thing over and over again, I cannot pass the login screen... there is no problem with password or anything like that, cause Im able to login starting with command line...
 
anyone knows what might be the problem here ? 
 
or how can I fix it, like re-installing something again without losing my data ??
 
thank-s in advance!!

---

### Post by vievgart on 2010-12-29
anyone ?

I guess it's a very uncommon problem... :/

---

### Post by tredegar on 2010-12-29
Lack of disk space will cause this.

ctrl-alt-F2
You get a terminal
login as yourself
then post the output of **df -h**

---

### Post by vievgart on 2010-12-29
edit

---

### Post by vievgart on 2010-12-29
edit

---

### Post by vievgart on 2010-12-29
hi tredegar,

thanks for your answer,

I did the login as you said, but it's definitely not a lack of space, the disk is big enough,

but on the login I could see something that can be the cause of the problem...
right after making login, It says:

[B][water]: command not found
-bash /home/myUserName/.profile: line 2: sintax error next to 'token' not expected '<'
-bash /home/myUserName/.profile: line 2: 'as_initiate_key' = <control><super>'[/B]


I was changing my compiz preferences before I reboot and having this problem...

so what can I do now ? 

I have to edit the file and try to fix the error ?

---

### Post by vievgart on 2010-12-29
hi, I just renamed the file .profile to .profile.bak and it solved the problem.

thanks for you're precious help.

---

### Post by borlosky on 2011-01-05
Just installed 10.10, clean install on older pc, isntall goes fine, able to login for first time, but after recommended updates, pc restarts, get login screen, login with user name/password, screen goes black, then back to login screen. also tried ctrl-alt-f2, then screen just goes black, no prompt comes up, can't type anything. so then i reinstalled/reformatted once more, exact same thing happens after updates. so now can't even get to a command prompt, and can't login at all.

---

### Post by Habitual on 2011-01-05
> **borlosky said:**
> ...tried ctrl-alt-f2, then screen just goes black, no prompt comes up, can't type anything....

That you can see? Does typing reset or reboot work under this condition?

---

### Post by borlosky on 2011-01-05
> **Habitual said:**
> That you can see? Does typing reset or reboot work under this condition?

no, can't type anything, just black screen

---

