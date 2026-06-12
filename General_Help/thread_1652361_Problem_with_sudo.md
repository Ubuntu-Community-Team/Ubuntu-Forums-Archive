---
title: "Problem with sudo"
date: 2010-12-24
forum: General Help
---

### Post by Ramy89 on 2010-12-24
Whenever I try to run something as root using the sudo comand I get:
```

ramy is not in the sudoers file.  This incident will be reported.

```

---

### Post by sisco311 on 2010-12-24
Boot into recovery mode and add your user to the admin group:

[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by garvinrick4 on 2010-12-24
> **Ramy89 said:**
> Whenever I try to run something as root using the sudo comand I get:
```

ramy is not in the sudoers file.  This incident will be reported.

```
post results:
```
gksudo gedit /etc/sudoers
```if it lets you open;
If not:
alt/f2
gksudo nautilus in box and hit enter
open file system go to etc and then sudoers file and open and Post.
##Post 2 looks like pretty good link.(just saw it)

---

### Post by WorMzy on 2010-12-24
> **garvinrick4 said:**
> post results:
```
gksudo gedit /etc/sudoers
```if it lets you open;
If not:
alt/f2
gksudo nautilus in box and hit enter
open file system go to etc and then sudoers file and open and Post.
##Post 2 looks like pretty good link.(just saw it)

?

The user is not in sudoers, so they cannot use sudo or, by extension, gksudo. You should never open /etc/sudoers like that anyway, it can lead to problems. Use "sudo cat" or "sudo less" to read the contents of a file which only allows root to read it, not gedit.

@OP: is this your PC? If not, contact the owner and ask to be added to the sudoers list. If it is, then log in as the first user you created (when you installed), or follow the instructions outlined in the link Sisco posted to recover your admin status.

---

### Post by garvinrick4 on 2010-12-24
#You are right WorMzy, I new sudo cat /etc/sudoers was no good in terminal for OP:
Was just trying to sneak in and get a peak if anyway possible to see if we could
fix quickly. Soon as I wrote it I saw link for post #2 was good place for OP to start.
#I honestly did not know opening in gksudo gedit was a problem for sudoers have used
vi but gedit was easier. Thanks for heads up been doing it for 3 years or so. 
#Should have thought maybe it could not be his machine. Will not mess with sudoers threads anymore with that in mind.
Have a Merry Christmas WorMzy and Ramy89.

---

### Post by Ramy89 on 2010-12-25
I ran ubuntu in recovery mode and wrote: adduser ramy admin,now it's all fine.

---

### Post by sisco311 on 2010-12-25
Cool!

Don't forget to mark this thread as [SOLVED].

---

